[![Docker Build Statu](https://img.shields.io/docker/build/hotio/suitarr.svg?style=flat-square)](https://hub.docker.com/r/hotio/suitarr)
[![Docker Automated buil](https://img.shields.io/docker/automated/hotio/suitarr.svg?style=flat-square)](https://hub.docker.com/r/hotio/suitarr)
[![Docker Pulls](https://img.shields.io/docker/pulls/hotio/suitarr.svg?style=flat-square)](https://hub.docker.com/r/hotio/suitarr)
[![Docker Stars](https://img.shields.io/docker/stars/hotio/suitarr.svg?style=flat-square)](https://hub.docker.com/r/hotio/suitarr)
[![Maintenance](https://img.shields.io/maintenance/yes/2018.svg?style=flat-square)](https://github.com/hotio/docker-suitarr)
[![Docker Build Status](https://img.shields.io/docker/build/vertigo235/suitarr.svg?style=flat-square)](https://hub.docker.com/r/vertigo235/suitarr)
[![Docker Automated build](https://img.shields.io/docker/automated/vertigo235/suitarr.svg?style=flat-square)](https://hub.docker.com/r/vertigo235/suitarr)
[![Docker Pulls](https://img.shields.io/docker/pulls/vertigo235/suitarr.svg?style=flat-square)](https://hub.docker.com/r/vertigo235/suitarr)
[![Docker Stars](https://img.shields.io/docker/stars/vertigo235/suitarr.svg?style=flat-square)](https://hub.docker.com/r/vertigo235/suitarr)

Donations: [xrb_3e4t96mw66ny1hupoo3c47xgqqy13q7htdyk7x7gf7nrbj635sx8hf5awe3c](https://raiblocks.net/account/index.php?acc=xrb_3e4t96mw66ny1hupoo3c47xgqqy13q7htdyk7x7gf7nrbj635sx8hf5awe3c)

```
    _________      __  __
   /   _____/__ __|__|/  |______ ______________
   \_____  \|  |  \  \   __\__  \\_  __ \_  __ \
   /        \  |  /  ||  |  / __ \|  | \/|  | \/
  /_______  /____/|__||__| (____  /__|   |__|
          \/                    \/
```

## What is Suitarr?

Suitarr is one docker image that can run Radarr, Sonarr, Lidarr, Jackett, NZBHydra, NZBHydra2 and NZBGet. By using the environment variable `-e APP=......`, the supported application will be downloaded and installed when starting the container.
This requires a lot less building of the images and all you need to do if you want to update the application is restart the container.

## Starting the container

The environment variables `PUID`, `PGID`, `UMASK`, `VERSION` and `BACKUP` are all optional, the values you see below are the default values. `APP` is required and can't be empty.

#### Radarr

```
docker run --rm \
           --name radarr \
           -p 7878:7878 \
           -e APP=radarr \
           -e PUID=1000 \
           -e PGID=1000 \
           -e UMASK=022 \
           -e VERSION=stable \
           -e BACKUP=yes \
           -v /etc/localtime:/etc/localtime:ro \
           -v /<local_path>/config:/config \
           hotio/suitarr
```

#### Sonarr

```
docker run --rm \
           --name sonarr \
           -p 8989:8989 \
           -e APP=sonarr \
           -e PUID=1000 \
           -e PGID=1000 \
           -e UMASK=022 \
           -e VERSION=stable \
           -e BACKUP=yes \
           -v /etc/localtime:/etc/localtime:ro \
           -v /<local_path>/config:/config \
           hotio/suitarr
```

#### Lidarr

```
docker run --rm \
           --name lidarr \
           -p 8686:8686 \
           -e APP=lidarr \
           -e PUID=1000 \
           -e PGID=1000 \
           -e UMASK=022 \
           -e VERSION=stable \
           -e BACKUP=yes \
           -v /etc/localtime:/etc/localtime:ro \
           -v /<local_path>/config:/config \
           hotio/suitarr
```

#### Jackett

```
docker run --rm \
           --name jackett \
           -p 9117:9117 \
           -e APP=jackett \
           -e PUID=1000 \
           -e PGID=1000 \
           -e UMASK=022 \
           -e VERSION=stable \
           -e BACKUP=yes \
           -v /etc/localtime:/etc/localtime:ro \
           -v /<local_path>/config:/config \
           hotio/suitarr
```

#### NZBHydra

```
docker run --rm \
           --name nzbhydra \
           -p 5075:5075 \
           -e APP=nzbhydra \
           -e PUID=1000 \
           -e PGID=1000 \
           -e UMASK=022 \
           -e VERSION=stable \
           -e BACKUP=yes \
           -v /etc/localtime:/etc/localtime:ro \
           -v /<local_path>/config:/config \
           hotio/suitarr
```

#### NZBHydra2

```
docker run --rm \
           --name nzbhydra2 \
           -p 5076:5076 \
           -e APP=nzbhydra2 \
           -e PUID=1000 \
           -e PGID=1000 \
           -e UMASK=022 \
           -e VERSION=stable \
           -e BACKUP=yes \
           -v /etc/localtime:/etc/localtime:ro \
           -v /<local_path>/config:/config \
           hotio/suitarr
```

#### NZBGet

```
docker run --rm \
           --name nzbget \
           -p 6789:6789 \
           -e APP=nzbget \
           -e PUID=1000 \
           -e PGID=1000 \
           -e UMASK=022 \
           -e VERSION=stable \
           -e BACKUP=yes \
           -v /etc/localtime:/etc/localtime:ro \
           -v /<local_path>/config:/config \
           hotio/suitarr
```

## Installing a different version

By default the latest stable version is installed. You can however change this behaviour with the environment variable `VERSION`.
The value `unstable` will install the latest unstable version, using a version number like `0.2.0.307` as a value, installs the specified version.
When given an absolute path like `/config/Radarr.develop.0.2.0.817.linux.tar.gz`, installs that local file.

#### Radarr

```
-e VERSION=unstable
-e VERSION=0.2.0.307
-e VERSION=/config/Radarr.develop.0.2.0.817.linux.tar.gz
```

#### Sonarr

```
-e VERSION=unstable
-e VERSION=2.0.0.4578
-e VERSION=/config/NzbDrone.develop.tar.gz
```

#### Lidarr

```
-e VERSION=unstable
-e VERSION=2.0.0.212
-e VERSION=/config/Lidarr.develop.0.2.0.212.linux.tar.gz
```

#### Jackett

```
-e VERSION=unstable
-e VERSION=0.7.1001
-e VERSION=/config/Jackett.Binaries.Mono.tar.gz
```

#### NZBHydra

```
-e VERSION=unstable
-e VERSION=f60a628cc5d2a17677e6c9b6bb12ad41063ea4e0
-e VERSION=/config/0.2.226.tar.gz
```

#### NZBHydra2

```
-e VERSION=unstable
-e VERSION=1.1.0
-e VERSION=/config/nzbhydra2-1.1.0-linux.zip
```

#### NZBGet

```
-e VERSION=unstable
-e VERSION=19.1-r2031
-e VERSION=/config/nzbget-19.1-bin-linux.run
```

## Backing up the configuration

By default on every docker container shutdown a backup is created from the configuration files.
To disable this, use `-e BACKUP=no`.

## Additional app arguments

You can use the following environment variable to pass on additional arguments to your app.

```
-e ARGS="--ProxyConnection localhost:8118"
```

#### for testing only, do not use unless you know what you are doing