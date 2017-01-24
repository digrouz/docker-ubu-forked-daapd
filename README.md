# docker-ubu-forkeddaapd
Install  Forked-daapd Server into an Ubuntu Linux Container

## Description
This is a Linux/FreeBSD DAAP (iTunes) and MPD media server with support for AirPlay devices, Apple Remote (and compatibles), Chromecast, Spotify and internet radio

http://ejurgensen.github.io/forked-daapd

## Usage
    docker create --name=forked-daapd  \
      -v /etc/localtime:/etc/localtime:ro \
      -v /var/run/dbus:/var/run/dbus \
      -v <path to music Library>:/srv/music \
      -e DOCKUID=<UID default:10013> \
      -e DOCKGID=<GID default:10013> \
      -p 3689:3689  digrouz/docker-ubu-forkeddaapd daapd


## Environment Variables

When you start the `forkeddaapd` image, you can adjust the configuration of the `forkeddaapd` instance by passing one or more environment variables on the `docker run` command line.

### `DOCKUID`

This variable is not mandatory and specifies the user id that will be set to run the application. It has default value `10013`.

### `DOCKGID`

This variable is not mandatory and specifies the group id that will be set to run the application. It has default value `10013`.

## Notes

* The docker entrypoint will upgrade operating system at each startup.
* It is assumed that the host is running the `dbus` daemon and share the socket through /var/run/dbus with this container. This is a requirement to have `mdns` support.


