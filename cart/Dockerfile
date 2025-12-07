FROM node:20
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
WORKDIR  /opt/app
COPY *.js *.json /opt/app/
RUN npm install
ENV REDIS_HOST="redis"
ENV CATALOGUE_HOST="catalogue"
ENV CATALOGUE_PORT="8080"
USER roboshop
EXPOSE 8080
CMD ["node", "server.js"]