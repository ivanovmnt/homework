FROM nginx:latest

# Update apt-get and install required packages
RUN apt-get update \
    && apt-get install -y \
    curl \
    gnupg2 \
    ca-certificates \
    php7.4-fpm \
    php7.4-cli \
    php7.4-common \
    php7.4-mysql \
    php7.4-mbstring \
    php7.4-xml \
    php7.4-curl \
    php7.4-gd \
    php7.4-zip \
    && apt-get clean

# Copy Nginx configuration and fpm default pool file to the container
COPY default.conf /etc/nginx/conf.d/default.conf
COPY www.conf /etc/php/7.4/fpm/pool.d/www.conf

#Create default doc root
RUN mkdir -p /var/www/html

# Start PHP-FPM and Nginx
CMD ["sh", "-c", "service php7.4-fpm start && nginx -g 'daemon off;'"]
