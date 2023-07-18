FROM httpd:2.4.48
COPY ./index.html /usr/local/apache2/htdocs/
RUN mkdir -p /usr/local/apache2/conf/custom/
COPY ./httpd.conf /usr/local/apache2/conf/httpd.conf
RUN chmod +r /usr/local/apache2/htdocs/index.html
