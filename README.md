rsync
=====

Simple rsync server running in a docker container

This is based off of https://github.com/nabeken/docker-volume-container-rsync with a few modifications. That project provides a volume for a docker mount, where as this provides just a simple, unauthenticated rsync server.

This is meant to be a temporary, disposable rsync storage. Do NOT use for backups. 

## Usage

Launch the container via docker:
```
docker run -d -p 873 -e "USERNAME:myuser" -e "PASSWORD:mypassword" bfosberry/rsync
```

You can connect to rsync server inside a container like this:

```sh
$ rsync rsync://<docker>:<port>/
data          data directory
```

To sync:

```sh
$ rsync -avP /path/to/dir rsync://<docker>:<port>/data/
```
