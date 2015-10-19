FROM buildpack-deps:jessie

MAINTAINER wencan <i@wencan.org>

ENV OPENRESTY_VERSION 1.9.3.1

RUN curl -Ls http://openresty.org/download/ngx_openresty-$OPENRESTY_VERSION.tar.gz | tar xzv \
    && cd ngx_openresty-* \
    && ./configure \
    && make \
    && make install \
    && rm -rf /ngx_openresty-* \
    && ln -s /usr/local/openresty/nginx/sbin/nginx /usr/local/bin/nginx

RUN ln -sf /dev/stdout /usr/local/openresty/nginx/logs/access.log
RUN ln -sf /dev/stderr /usr/local/openresty/nginx/logs/error.log

EXPOSE 80 443

CMD ["nginx", "-g", "daemon off;"]
