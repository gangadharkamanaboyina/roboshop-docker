FROM node:20.19-alpine
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
WORKDIR  /opt/app
COPY *.js *.json /opt/app/
RUN npm install
ENV REDIS_URL="redis://redis:6379" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
USER roboshop
EXPOSE 8080
CMD ["node", "server.js"]