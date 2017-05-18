FROM bitnami/minideb-extras:jessie-r15
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages libapr1 libaprutil1 libbz2-1.0 libc6 libcomerr2 libcurl3 libexpat1 libffi6 libfreetype6 libgcc1 libgcrypt20 libgmp10 libgnutls-deb0-28 libgpg-error0 libgssapi-krb5-2 libhogweed2 libicu52 libidn11 libjpeg62-turbo libk5crypto3 libkeyutils1 libkrb5-3 libkrb5support0 libldap-2.4-2 liblzma5 libmcrypt4 libncurses5 libnettle4 libp11-kit0 libpcre3 libpng12-0 libpq5 libreadline6 librtmp1 libsasl2-2 libssh2-1 libssl1.0.0 libstdc++6 libsybdb5 libtasn1-6 libtidy-0.99-0 libtinfo5 libuuid1 libxml2 libxslt1.1 zlib1g
RUN bitnami-pkg unpack apache-2.4.25-0 --checksum 8b46af7d737772d7d301da8b30a2770b7e549674e33b8a5b07480f53c39f5c3f
RUN bitnami-pkg unpack php-5.6.30-3 --checksum af6c238825d4394fc6352c5ad48c1e6423e21520df927097dab592f0d4ad4662
RUN bitnami-pkg unpack mysql-client-10.1.23-1 --checksum 0be92fcc4f7fec93edfa7f788e2bbb87b5b3aac92dfdec159a10590345362512
RUN bitnami-pkg install libphp-5.6.30-1 --checksum a62cad2320fa2d141309e75663aed3d1bd82626d51b784678d18ec3f985d83bf
RUN bitnami-pkg unpack sugarcrm-6.5.25-0 --checksum 3b1ba7b8dd6cb00d31708e07b0785dd1da5f50167ad7046ba7307bb8fa25b093

COPY rootfs /

ENV ALLOW_EMPTY_PASSWORD="no" \
    APACHE_HTTPS_PORT="443" \
    APACHE_HTTP_PORT="80" \
    BITNAMI_APP_NAME="sugarcrm" \
    BITNAMI_IMAGE_VERSION="6.5.25-r3" \
    MARIADB_HOST="mariadb" \
    MARIADB_PASSWORD="" \
    MARIADB_PORT="3306" \
    MARIADB_ROOT_PASSWORD="" \
    MARIADB_ROOT_USER="root" \
    MARIADB_USER="root" \
    MYSQL_CLIENT_CREATE_DATABASE_NAME="" \
    MYSQL_CLIENT_CREATE_DATABASE_PASSWORD="" \
    MYSQL_CLIENT_CREATE_DATABASE_PRIVILEGES="ALL" \
    MYSQL_CLIENT_CREATE_DATABASE_USER="" \
    PATH="/opt/bitnami/apache/bin:/opt/bitnami/php/bin:/opt/bitnami/mysql/bin:$PATH" \
    SUGARCRM_EMAIL="user@example.com" \
    SUGARCRM_HOST="127.0.0.1" \
    SUGARCRM_LAST_NAME="Name" \
    SUGARCRM_PASSWORD="bitnami" \
    SUGARCRM_SMTP_HOST="" \
    SUGARCRM_SMTP_PASSWORD="" \
    SUGARCRM_SMTP_PORT="" \
    SUGARCRM_SMTP_PROTOCOL="" \
    SUGARCRM_SMTP_USER="" \
    SUGARCRM_USER_NAME="User"

VOLUME ["/bitnami/apache","/bitnami/php","/bitnami/sugarcrm"]

EXPOSE 80 443

ENTRYPOINT ["/app-entrypoint.sh"]
CMD ["/run.sh"]
