# hello-wsgi:
#### It's a simple *'hello world'* app based on **uwsgi** and **Python3**.
---


### Deploy?
#### You must set up a *virtualenv* with Python3 and uwsgi. It'll be easier if you use [virtualenvwrapper](https://wiki.archlinux.org/index.php/Python/Virtual_environment#virtualenvwrapper):

```
# mkvirtualenv --python="/usr/bin/python3" -i uwsgi venv
```

<br />


### Ok, now what?
#### You must have noticed that if you've used *virtualenvwrapper* to create a new *venv*, it will activate your *venv* for you. So, once inside your *venv*, all you have to do is run our *'uwsgi.ini'* file:

```
# uwsgi --ini="uwsgi.ini"
```

<br />

### Running, but...
#### I have to explain it all, right? Ok, ok! If no errors have shown, go to your web browser and check http://localhost:8080 .
#### It's important to take a look at our *'uwsgi.ini'* file:

<br />

```
[uwsgi]

chdir           = %v
#               '%v' indicated the vassals directory (pwd)

pidfile         = /tmp/uwsgi.pid
#               You can kill it using 'kill $(cat /tmp/uwsgi.pid)'

http            = 0.0.0.0:8080
#               You can use a socket file instead:
#               socket         = /tmp/uwsgi.sock

chmod-socket    = 666

module         = hello
#               Instead of 'module' you can also use:
#               wsgi-file       = hello.py


vacuum          = true
#               'vacuum' will clear the socket file 

daemonize       = hello_daemon.log                                 
```

### Beyond:
#### pip install flask
#### =)

<br />

# That's all folks!
