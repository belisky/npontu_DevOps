FROM php:7.4-apache
RUN docker-php-ext-install mysqli

RUN a2enmod rewrite
COPY index.html /var/www/html/
COPY .htaccess /var/www/html/ 

EXPOSE 80

CMD ["apache2-foreground"]

 
 
 
 
