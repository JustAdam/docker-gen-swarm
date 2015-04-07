FROM ubuntu:14.04

MAINTAINER JustAdam <adambell7@gmail.com>

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get clean && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y nginx

# Log to stdout/stderr
RUN sed -i -e "/access_log/i log_format site_combined '\$host> \$remote_addr - \$remote_user [\$time_local] \"\$request\" \$status \$body_bytes_sent \"\$http_referer\" \"\$http_user_agent\"';" /etc/nginx/nginx.conf
RUN sed -i -e "s/\/var\/log\/nginx\/access.log/\/dev\/stdout site_combined/g" /etc/nginx/nginx.conf
RUN sed -i -e "s/\/var\/log\/nginx\/error.log/\/dev\/stderr/g" /etc/nginx/nginx.conf
RUN echo "\ndaemon off;" >> /etc/nginx/nginx.conf

EXPOSE 80

CMD ["nginx"]
