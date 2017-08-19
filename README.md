# Dockerized HAProxy with Let's Encrypt

This container provides a HAProxy 1.7 application with Let's Encrypt certificates
generated at startup, as well as renewed (if necessary) once a week.
It also provide stats, logging.

## Usage

```
docker run \
    -e CERTS=my.domain,my.other.domain \
    -e EMAIL=my.email@my.domain \
    -v /etc/letsencrypt:/etc/letsencrypt \
    -p 80:80 -p 443:443 \
    gpoudrel/docker-haproxy-letsencrypt
```

You will almost certainly want to create an image `FROM` this image or
mount your `haproxy.cfg` at `/usr/local/etc/haproxy/haproxy.cfg`.

### Display logs
```
docker exec -i -t yourcontainernameorid tail -f /var/log/haproxy.log
```

You will almost certainly want to mount a volume to have your log file outside of container.

### Alternatives

HAProxy is powerful, but notoriously difficult to configure. If you don't require
HAProxy's functionality per se, consider [this similar image for Nginx](https://github.com/BradJonesLLC/docker-nginx-letsencrypt).

### License and Copyright
&copy; Gregory Poudrel, Licensed under GPL-2. Some components MIT license.

Original author: &copy; Brad Jones LLC, Licensed under GPL-2. Some components MIT license.
