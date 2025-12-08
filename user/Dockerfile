FROM node:20.19-alpine AS builder
WORKDIR  /opt/app
COPY *.js *.json /opt/app/
RUN npm install

FROM node:20.19-alpine
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
WORKDIR /opt/app
LABEL project="roboshop" \
      component="catalogue"
ENV REDIS_URL="redis://redis:6379" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
EXPOSE 8080
COPY --from=builder --chown=roboshop:roboshop /opt/app /opt/app/
USER roboshop
CMD ["node", "server.js"]



# FROM node:20.19-alpine
# RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
# WORKDIR  /opt/app
# COPY *.js . 
# COPY *.json .
# RUN npm install
# ENV REDIS_URL="redis://redis:6379" \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# USER roboshop
# EXPOSE 8080
# CMD ["node", "server.js"]