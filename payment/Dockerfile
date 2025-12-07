FROM python:3.12-alpine
EXPOSE 8080
WORKDIR /opt/app
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
USER roboshop
COPY *.py /opt/app/ \
     payment.ini /opt/app/ \
     requirements.txt /opt/app/
RUN pip3 install -r requirements.txt
ENV CART_HOST="cart" \
    CART_PORT="8080" \
    USER_HOST="user" \
    USER_PORT="8080" \
    AMQP_HOST="rabbitmq" \
    AMQP_USER="roboshop" \
    AMQP_PASS=roboshop123
CMD [ "uwsgi", "--ini", "payment.ini" ]
