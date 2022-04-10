# docker build -t wordsmithjvm .
# docker run wordsmithjvm
# docker run -ti wordsmithjvm bash

FROM ubuntu

# Install the JDK and Maven, as instructed.
RUN apt-get update
RUN apt-get install maven openjdk-8-jdk -y

# can also do WORKDIR
# WORKDIR /src
# COPY pom.xml .
# COPY src src

# Copy all the files. This is not optimal, but it
# will do for now.
# COPY . .
# or
COPY pom.xml .
COPY src src

# Build the code. Note: this will place multiple
# JAR files in a directory named "target". There
# will be our compiled code ("words.jar") but also
# its dependencies.
RUN mvn verify

# We use the "exec" shell built-in here, to make
# sure that the program executes as PID 1 and
# therefore receives signals correctly.
CMD exec java -Xmx8m -Xms8m -jar target/words.jar