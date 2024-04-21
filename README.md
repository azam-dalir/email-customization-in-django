***environs and secret-key***

1-install environs package in docker-compose and venv with this code:

    docker-compose exec web pip install "environs[django]"
    docker-compose exec web pip freeze > requirements.txt
    pip install -r requirements.txt

2-import Env in settings.py:

    from environs import Env

    # for environs env
    env = Env()
    env.read_env()

3-set DJANGO-SECRET-KEY in settings.py:

    SECRET_KEY = env("DJANGO_SECRET_KEY")

4-set SECRET-KEY in Docker-compose.yml:

    depends_on:
      - db
    environment:
      - "DJANGO_SECRET_KEY=[django-insecure-code in setting.py]"

***email customization in django***

1-The SMTP backend is the default configuration inherited by Django. If you want to specify it explicitly, put the following in your settings.py:

    EMAIL_BACKEND = "django.core.mail.backends.smtp.EmailBackend"
    
2-This is the default backend. Email will be sent through a SMTP server.add this code in settings.py

    EMAIL_HOST = 'smtp.gmail.com'
    EMAIL_USE_TLS = True
    EMAIL_PORT = 587
    EMAIL_HOST_USER = 'your_account@gmail.com'
    EMAIL_HOST_PASSWORD = 'your account password'
    
