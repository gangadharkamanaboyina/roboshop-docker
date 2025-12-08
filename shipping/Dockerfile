FROM maven:3.9.11 AS builder
WORKDIR /opt/app
COPY pom.xml .
COPY src ./src 
RUN mvn clean package && \
    mv target/shipping-1.0.jar shipping.jar 

FROM eclipse-temurin:17-jre-alpine
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
USER roboshop
ENV CART_ENDPOINT="cart:8080" \
    DB_HOST="mysql"
COPY --from=builder --chown=roboshop:roboshop /opt/app/shipping.jar .
CMD [ "java", "-jar", "shipping.jar" ]

# FROM maven:3.9.11
# EXPOSE 8080
# # RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
# # USER roboshop
# WORKDIR /opt/app
# COPY pom.xml .
# COPY src ./src 
# RUN mvn clean package 
# RUN mv target/shipping-1.0.jar shipping.jar 
# ENV CART_ENDPOINT="cart:8080" \
#     DB_HOST="mysql"
# CMD [ "java", "-jar", "shipping.jar" ]