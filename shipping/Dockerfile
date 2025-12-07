FROM maven:3.9.11
EXPOSE 8080
RUN groupadd -r roboshop && useradd -r -g roboshop roboshop
USER roboshop
WORKDIR /opt/app
COPY src ./src \
     pom.xml ./
RUN mvn clean package \
    mv target/shipping-1.0.jar shipping.jar 
ENV CART_ENDPOINT="cart:8080" \
    DB_HOST="mysql"
CMD [ "java", "-jar", "shipping.jar" ]