FROM maven:3.6.2-jdk-11-slim AS MAVEN_TOOL_CHAIN
COPY pom.xml /tmp/
COPY src /tmp/src/
WORKDIR /tmp/
RUN mvn package -Pprod -DskipTests

FROM openjdk:11.0.4-jre
COPY --from=MAVEN_TOOL_CHAIN /tmp/target/user-administration-0.0.1-SNAPSHOT.jar /user-admin.jar
CMD /usr/local/openjdk-11/bin/java -Daplication-secret=secret -jar /user-admin.jar