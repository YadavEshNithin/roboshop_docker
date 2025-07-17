FROM nginx:1.24
RUN rm -rf /usr/share/nginx/html/index.html
COPY *.html /usr/share/nginx/html/
COPY css /usr/share/nginx/html/css/.
COPY images /usr/share/nginx/html/images/.
COPY media /usr/share/nginx/html/media/.
RUN rm -rf /etc/nginx/nginx.conf
RUN rm -rf /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/
