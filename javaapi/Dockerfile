FROM maven:sapmachine as build_image
WORKDIR /usr/src/app/
RUN apt update && apt install openjdk-21-jdk -y
COPY ./ /usr/src/app/
RUN mvn install -DskipTests

FROM maven:sapmachine

WORKDIR /usr/src/app/
COPY --from=build_image /usr/src/app/target/book-work-0.0.1-SNAPSHOT.jar ./book-work-0.0.1.jar

EXPOSE 9000
ENTRYPOINT ["java","-jar","book-work-0.0.1.jar"]
# Test
