FROM ubuntu:14.04

MAINTAINER JustAdam <adambell7@gmail.com>

RUN apt-get update &&     apt-get upgrade -y &&     apt-get clean

ADD docker-gen /usr/bin/docker-gen

ADD certs/ /certs/

RUN mkdir -p /etc/docker-gen
ADD templates/nginx.tmpl /etc/docker-gen/nginx.tmpl

RUN mkdir -p /etc/nginx/sites-enabled
ADD sites-enabled/ /etc/nginx/sites-enabled/

VOLUME ["/etc/docker-gen/", "/etc/nginx/sites-enabled/"]
WORKDIR /etc/docker-gen/

CMD ["/usr/bin/docker-gen", "--tlscacert=/certs/ca.pem", "--tlscert=/certs/cert.pem", "--tlskey=/certs/key.pem", "-watch", "-only-exposed", "-notify-sighup=dockergenswarm_nginx_1 ", "nginx.tmpl", "/etc/nginx/sites-enabled/reverse-proxy"]
