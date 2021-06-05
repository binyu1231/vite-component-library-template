# python flask boilerplate

## Startup

``` bash
$ python3 -m venv venv

$ source venv/bin/activate # linux: 
$ venv\Scripts\activate # windows: 

(venv)$ pip install -r requirements.txt

$ sqlite3
> .open db.sqlite
> .databases # to check
> .quit
```

### develop

``` python
from app import app

if __name__ == '__main__':
  # Development
  app.run(debug=True, host = host, port = port)
```

``` bash
(venv)$ python main.py
```

### deploy

``` python
from gevent.pywsgi import WSGIServer
from app import app

if __name__ == '__main__':
  # Production
  http_server = WSGIServer(('0.0.0.0', port), app)
  http_server.serve_forever()
```

1. supervisor

``` bash
# /etc/supervisord.d/<project>.ini

command   = /usr/bin/python /home/www/<project>/main.py
directory = /home/www/<project>/
```

```bash
$ supervisorctl start <project>
$ supervisorctl shutdown
```

2. docker

``` bash
$ docker compose up -d
```

Note: Configure Database.

`<doing>`

## install packages

``` bash
(venv)$ pip install <package>
(venv)$ pip freeze > requirements.txt
```

## Feature

- [x] configure env for Development, Testing and Production
  - `config`
- [x] route's demo 
  - `application.routes.demo`
- [x] SQLAlchemy's demo with sqlite 
  - `application.models.user` 
  - `application.models.role` 
  - `application.routes.user`
  - `application.routes.role`
  - `application.routes.access`
- [ ] schedule's demo
- [ ] permissions
- [x] JWT for RESTful
- [x] Insomnia.yaml for HTTP Client [Insomnia](https://insomnia.rest/)
- [x] for docker


## Lib

- [Flask-JWT](https://pythonhosted.org/Flask-JWT/)