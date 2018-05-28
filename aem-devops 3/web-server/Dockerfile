FROM httpd:2.4

COPY ./public-html/ /usr/local/apache2/htdocs/
RUN chown www-data:www-data -R /usr/local/apache2/htdocs/
COPY ./conf/httpd.conf /usr/local/apache2/conf/httpd.conf
COPY ./conf/vhosts /usr/local/apache2/conf/vhosts
