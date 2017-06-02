
[install](https://github.com/vitorfs/bootcamp/wiki/Installing-and-Running-Bootcamp)

#### create virtual env
```
    virtualenv venv
    venv\Scripts\activate
    (env) e:\
```


####  Install dependencies
```
    (env) pip install -U -r requirements.txt
```


#### update db settings
```
    # file ".env"

    DEBUG=True
    SECRET_KEY=s3cr3t_key
    DATABASE_URL=mysql://root:rootadmin@localhost:3306/opencv
    ALLOWED_HOSTS=*
```



#### Syncdb
```
    (env) python manage.py migrate
```

#### Run
```
    (env) python manage.py runserver
```


### deploy to apache 

#### copy static files
```
    (env) python manage.py collectstatic
```

#### apache mod_wsgi setting 
```
    LoadModule wsgi_module "E:\env\Lib\site-packages\mod_wsgi\server\mod_wsgi.cp36-win_amd64.pyd"

    WSGIScriptAlias / "E:\source\django-sample-app\bootcamp\bootcamp\wsgi.py"
    WSGIPythonHome "E:\source\django-sample-app\venv"
    WSGIPythonPath "E:\source\django-sample-app\bootcamp"

    <VirtualHost *:80>
        ServerName www.example.com
        
        <Directory "E:\source\django-sample-app\bootcamp\bootcamp">
            Require all granted
        </Directory>
        
        Alias /static "E:\source\django-sample-app\bootcamp\staticfiles"
        <Directory "E:\source\django-sample-app\bootcamp\staticfiles">
            Require all granted
        </Directory>

    </VirtualHost>
``` 


## Installation Guide

Take a look at our wiki page for a detailed [installation guide][3].


## Demo

Try Bootcamp now at [http://trybootcamp.vitorfs.com][2].

[0]: https://www.python.org/
[1]: https://www.djangoproject.com/
[2]: http://trybootcamp.vitorfs.com/
[3]: https://github.com/vitorfs/bootcamp/wiki/Installing-and-Running-Bootcamp
