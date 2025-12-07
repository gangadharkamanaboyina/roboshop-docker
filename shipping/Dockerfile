FROM maven:3.9.11
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
USER roboshop
WORKDIR /opt/app
COPY src /opt/app/src \
     pom.xml /opt/app/
RUN mvn clean package \
    mv target/shipping-1.0.jar shipping.jar 
ENV CART_ENDPOINT="cart:8080" \
    DB_HOST="mysql"
CMD [ "java", "-jar", "shipping.jar" ]