FROM alpine:latest
MAINTAINER HQM 

ENV NGINX_VERSION 1.26.0

RUN	apk update		&&	\
	apk add				\
		git			\
		gcc			\
		binutils-dev		\
		binutils		\
		gmp			\
		isl-dev			\
		libgomp			\
		libatomic		\
		libgcc			\
		openssl			\
		pkgconf			\
		pkgconfig		\
		mpc1			\
		libstdc++		\
		ca-certificates		\
		libssh2			\
		curl			\
		expat			\
		pcre			\
		musl-dev		\
		libc-dev		\
		pcre-dev		\
		zlib-dev		\
		openssl-dev		\
		make


RUN	cd /tmp/									&&	\
	wget http://nginx.org/download/nginx-${NGINX_VERSION}.tar.gz			&&	\
	git clone https://github.com/wandenberg/nginx-push-stream-module.git

RUN	cd /tmp										&&	\
	tar xzf nginx-${NGINX_VERSION}.tar.gz						&&	\
	cd nginx-${NGINX_VERSION}							&&	\
	./configure										\
		--prefix=/opt/nginx								\
		--with-http_ssl_module								\
		--add-module=../nginx-push-stream-module		&&	\
	make										&&	\
	make install

RUN	cd /opt/ 	&&	\
	tar cvzf /tmp/nginx.tar.gz nginx

EXPOSE 80

CMD ["/opt/nginx/sbin/nginx", "-g", "daemon off;"]

