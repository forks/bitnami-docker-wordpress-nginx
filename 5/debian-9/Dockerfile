FROM bitnami/minideb-extras:stretch-r222
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages libbz2-1.0 libc6 libcomerr2 libcurl3 libffi6 libfreetype6 libgcc1 libgcrypt20 libgmp10 libgnutls30 libgpg-error0 libgssapi-krb5-2 libhogweed4 libicu57 libidn11 libidn2-0 libjpeg62-turbo libk5crypto3 libkeyutils1 libkrb5-3 libkrb5support0 libldap-2.4-2 liblzma5 libmemcached11 libmemcachedutil2 libncurses5 libnettle6 libnghttp2-14 libp11-kit0 libpcre3 libpng16-16 libpq5 libpsl5 libreadline7 librtmp1 libsasl2-2 libssh2-1 libssl1.0.2 libssl1.1 libstdc++6 libsybdb5 libtasn1-6 libtidy5 libtinfo5 libunistring0 libxml2 libxslt1.1 zlib1g
RUN bitnami-pkg unpack nginx-1.14.2-20 --checksum b9c38f5825b9f7b9625e0aa0ec38d8d4849504b4657bdbcbd6c1ddc0afa18596
RUN bitnami-pkg unpack php-7.2.13-20 --checksum e20ff2dcb16cc1fbd9adaebf2583a13d3f76d62c1ad599b27891a2ef04fa5e94
RUN bitnami-pkg install wp-cli-2.0.1-1 --checksum f629173f94034e309db4bfaed1bd84a86db88660c71829cfb65a754ce9276a05
RUN bitnami-pkg unpack mysql-client-10.2.19-21 --checksum 6f1768760f67b535d4eca3518bfec1dba6a05de113cf6e7c26a93fc129395e83
RUN bitnami-pkg unpack wordpress-5.0.1-2 --checksum 0f3c0b1b7126f600c62056a9518654ef6d8163df41522bb685eeed1e28c5cec5
RUN ln -sf /dev/stdout /opt/bitnami/nginx/logs/access.log
RUN ln -sf /dev/stderr /opt/bitnami/nginx/logs/error.log

COPY rootfs /
ENV ALLOW_EMPTY_PASSWORD="no" \
    BITNAMI_APP_NAME="wordpress-nginx" \
    BITNAMI_IMAGE_VERSION="5.0.1-debian-9-r2" \
    MARIADB_HOST="mariadb" \
    MARIADB_PORT_NUMBER="3306" \
    MARIADB_ROOT_PASSWORD="" \
    MARIADB_ROOT_USER="root" \
    MYSQL_CLIENT_CREATE_DATABASE_NAME="" \
    MYSQL_CLIENT_CREATE_DATABASE_PASSWORD="" \
    MYSQL_CLIENT_CREATE_DATABASE_PRIVILEGES="ALL" \
    MYSQL_CLIENT_CREATE_DATABASE_USER="" \
    NGINX_DAEMON_GROUP="daemon" \
    NGINX_DAEMON_USER="daemon" \
    NGINX_HTTPS_PORT_NUMBER="443" \
    NGINX_HTTP_PORT_NUMBER="80" \
    PATH="/opt/bitnami/nginx/sbin:/opt/bitnami/php/bin:/opt/bitnami/php/sbin:/opt/bitnami/wp-cli/bin:/opt/bitnami/mysql/bin:$PATH" \
    SMTP_HOST="" \
    SMTP_PASSWORD="" \
    SMTP_PORT="" \
    SMTP_PROTOCOL="" \
    SMTP_USER="" \
    SMTP_USERNAME="" \
    WORDPRESS_BLOG_NAME="User's Blog!" \
    WORDPRESS_DATABASE_NAME="bitnami_wordpress" \
    WORDPRESS_DATABASE_PASSWORD="" \
    WORDPRESS_DATABASE_USER="bn_wordpress" \
    WORDPRESS_EMAIL="user@example.com" \
    WORDPRESS_FIRST_NAME="FirstName" \
    WORDPRESS_HOST="" \
    WORDPRESS_HTTPS_PORT="443" \
    WORDPRESS_HTTP_PORT="80" \
    WORDPRESS_LAST_NAME="LastName" \
    WORDPRESS_PASSWORD="bitnami" \
    WORDPRESS_TABLE_PREFIX="wp_" \
    WORDPRESS_USERNAME="user"

EXPOSE 80 443

ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "./run.sh" ]
