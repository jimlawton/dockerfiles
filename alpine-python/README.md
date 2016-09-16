# alpine-python

[hub]: https://hub.docker.com/r/jlawton/dockerfiles/alpine-python/

A small Python Docker image based on [Alpine Linux](http://alpinelinux.org/). The image is only 225 MB and it includes `python3-dev`. Based on [jfloff's original work](https://github.com/jfloff/alpine-python).

## Supported tags
* **2.7 ([Dockerfile](https://github.com/jlawton/alpine-python/blob/master/2.7/Dockerfile))**
* **2.7-onbuild ([Dockerfile](https://github.com/jlawton/alpine-python/blob/master/2.7/onbuild/Dockerfile))**
* **3.5 ([Dockerfile](https://github.com/jlawton/alpine-python/blob/master/3.5/Dockerfile))**
* **3.5-onbuild ([Dockerfile](https://github.com/jlawton/alpine-python/blob/master/3.5/onbuild/Dockerfile))**

**NOTE:** `onbuild` images install the `requirements.txt` of your project from the get go. This allows you to cache your requirements right in the build. _Make sure you are in the same directory of your `requirements.txt` file_.

## Why?
The default docker python images are too [big](https://github.com/docker-library/python/issues/45).

## Usage
This image runs `python` command on `docker run`. You can either specify your own command, e.g:
```shell
$ docker run --rm -ti jlawton/alpine-python python hello.py
```

Or extend this images using your custom `Dockerfile`, e.g:
```dockerfile
FROM jlawton/alpine-python:3.4-onbuild

# for a flask server
EXPOSE 5000
CMD python manage.py runserver
```

Dont' forget to build _your_ image:
```shell
$ docker build --rm=true -t jlawton/app .
```

You can also access `bash` inside the container:
```shell
$ docker run --rm -ti jlawton/alpine-python /bin/bash
```

You can build an extended `Dockerfile` version (like shown above), and mount your specific application inside the container:
```shell
$ docker run --rm -v "$(pwd)":/home/app -w /home/app -p 5000:5000 -ti jlawton/app
```

## Details
* Installs `python-dev` allowing the use of more advanced packages such as `gevent`
* Installs `bash` allowing interaction with the container
* Just like the main `python` docker image, it creates useful symlinks that are expected to exist, e.g. `python3.4` > `python`, `pip2.7` > `pip`, etc.)
* Added `testing` repository to Alpine's `/etc/apk/repositories` file


## License
The code in this repository, unless otherwise noted, is MIT licensed. See the `LICENSE` file in this repository.
