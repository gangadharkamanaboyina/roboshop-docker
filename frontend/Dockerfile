FROM nginx:1.24.0-alpine
WORKDIR /opt/app/
RUN rm -rf /usr/share/nginx/html/*
COPY static /usr/share/nginx/html/
RUN rm -rf /etc/nginx/nginx.conf
COPY nginx.conf /etc/nginx/nginx.conf
CMD ["nginx", "-g", "daemon off;"]
