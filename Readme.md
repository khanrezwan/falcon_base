Trying Python Falcon framework + RethinkDB+ with PyPy interpreter. used this [Tutoial](https://impythonist.wordpress.com/2015/09/12/build-massively-scalable-restful-api-with-falcon-and-pypy/)
### Install PyPy
* Download PyPy interpreter from [here](http://pypy.org/download.html)
* install as following
```sh
$ tar -xvjf pypy2-v5.6.0-linux64.tar.bz2
$ sudo mv pypy2-v5.6.0-linux64 /opt
$ sudo ln -s /opt/pypy2-v5.6.0-linux64/bin/pypy /usr/local/bin/
```

###Install RethinkDB
```sh
$ source /etc/lsb-release && echo "deb http://download.rethinkdb.com/apt $DISTRIB_CODENAME main" | sudo tee /etc/apt/sources.list.d/rethinkdb.list
$ wget -qO- https://download.rethinkdb.com/apt/pubkey.gpg | sudo apt-key add -
$ sudo apt-get update
$ sudo apt-get install rethinkdb
$ sudo cp /etc/rethinkdb/default.conf.sample /etc/rethinkdb/instances.d/instance1.conf
$ sudo service rethinkdb start
```

###Create Project
I will be using virtualenv.

```sh
$ mkdir falcon_test
$ cd falcon_test
$ virtualenv -p pypy venv
$ source venv/bin/activate
$ pip install rethinkdb falcon gunicorn pylint
$ pip freeze > requirements.txt
```

###Visual Code Studio setup
* from command pallete choose Python: Select Workspace Interpreter
* select ./venv/bin/python
* in the folder .vscode open settings.json
* change "python.pythonPath": "${workspaceRoot}/venv/bin/python" ->  "python.pythonPath": "${workspaceRoot}/venv/bin/pypy"

### To Run

```sh
$ gunicorn app:api
```
