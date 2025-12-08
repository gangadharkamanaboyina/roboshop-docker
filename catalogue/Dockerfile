FROM node:20.19-alpine AS builder
WORKDIR  /opt/app
COPY *.js *.json /opt/app/
RUN npm install

FROM node:20.19-alpine
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
WORKDIR /opt/app
LABEL project="roboshop" \
      component="catalogue"
ENV mongo="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
EXPOSE 8080
COPY --from=builder --chown=roboshop:roboshop /opt/app /opt/app/
USER roboshop
CMD ["node", "server.js"]