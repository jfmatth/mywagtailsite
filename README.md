# My Wagtail site

First attempt at following the tutorial and then dockerizing for local and K8s usage.

## Building images for Podman
We will use the build powershell script to build our image locall, need two files:
- IMAGE - the ghcr.io path for the image  
- VERSION - the tag we'll put on the image  

```
build
```


## Running

Wagtail ```DJANGO_SETTINGS_MODULE``` defaults to ```core.dev.py```

### Locally
Just Django ```runserver``` nothing fancy.

### Podman local
docker-compose for the win here

```
podman compose up --build
```

Migrate the DB
```
podman exec -it mywagtailsite-web-1 python manage.py migrate --no-input
```

Create a super user
```
podman exec -it mywagtailsite-web-1  python manage.py createsuperuser
```