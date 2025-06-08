FROM php:8.1-apache

# Install MySQL server & PHP extensions
RUN apt-get update && \
    apt-get install -y default-mysql-server default-mysql-client && \
    docker-php-ext-install mysqli pdo pdo_mysql && \
    service mysql start

# Enable Apache mod
RUN a2enmod rewrite

# Copy sample index file
COPY index.php /var/www/html/

# Start Apache and MySQL
CMD service mysql start && apache2-foreground

# Download phpMyAdmin
RUN apt-get install -y unzip wget && \
    wget https://files.phpmyadmin.net/phpMyAdmin/5.2.1/phpMyAdmin-5.2.1-all-languages.zip && \
    unzip phpMyAdmin-5.2.1-all-languages.zip && \
    mv phpMyAdmin-5.2.1-all-languages /var/www/html/phpmyadmin
