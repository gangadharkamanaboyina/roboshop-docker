FROM node:20.19-alpine
WORKDIR  /opt/app
COPY *.js *.json /opt/app/
RUN npm install

FROM node:20.19-alpine
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
WORKDIR /opt/app
USER roboshop
COPY --from=builder --chown=roboshop:roboshop /opt/app /opt/app/
ENV mongo="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
USER roboshop
EXPOSE 8080
CMD ["node", "server.js"]
