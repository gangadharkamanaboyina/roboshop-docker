FROM node:20.19-alpine AS builder
WORKDIR  /opt/app
COPY *.js *.json /opt/app/
RUN npm install

FROM node:20.19-alpine
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
WORKDIR /opt/app
LABEL project="roboshop" \
      component="catalogue"
ENV REDIS_HOST="redis" \
    CATALOGUE_HOST="catalogue" \
    CATALOGUE_PORT="8080"
EXPOSE 8080
COPY --from=builder --chown=roboshop:roboshop /opt/app /opt/app/
USER roboshop
CMD ["node", "server.js"]




# FROM node:20.19-alpine
# RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
# WORKDIR  /opt/app
# COPY *.js *.json /opt/app/
# RUN npm install
# ENV REDIS_HOST="redis"
# ENV CATALOGUE_HOST="catalogue"
# ENV CATALOGUE_PORT="8080"
# USER roboshop
# EXPOSE 8080
# CMD ["node", "server.js"]