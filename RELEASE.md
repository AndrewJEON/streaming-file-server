# streaming-file-server

_version: 4.3.3_

## Java file server 

**Java file server** based on *spring-boot* with no memory, upload or download files size limitations

- Update spring-boot up to 2.0.3.RELEASE
- Update gradle up to 4.9
- Add Gradle Lombok plugin
- Add pom.xml + wrapper with jutzig/github-release-plugin configuration. Just run: `./mvnw`
- Add maven asciidoctor plugin documentation automation. Run command: `./mvnw -Pdocs`

## Installation

### with postgres database

#### manual

```bash
# docker compose file for postgres database
wget https://github.com/daggerok/streaming-file-server/releases/download/4.3.3/docker-compose.yml
docker-compose up -d

# file-items data service
wget https://github.com/daggerok/streaming-file-server/releases/download/4.3.3/file-items-service-4.3.3.jar
java -jar file-items-service-4.3.3.jar --spring.profiles.active=db-pg

# file server
wget https://github.com/daggerok/streaming-file-server/releases/download/4.3.3/file-server-4.3.3.jar
java -jar file-server-4.3.3.jar --app.upload.path=./path/to/file-storage

# cleanup
docker-compose down -v
```

#### or for simplicity use automation shell-script (*nix)

```bash
# bash script
wget https://github.com/daggerok/streaming-file-server/releases/download/4.3.3/application.bash

# start
bash application.bash start ./path/to/file-storage

# stop
bash application.bash stop

# cleanup
bash application.bash clean ./path/to/file-storage
```

*note: tested on osx with docker installed locally*

binaries: `wget`, `docker-compose`, `bash` and of course `java` are required

#### same automation on windows

```cmd
@rem batch shell-script
wget https://github.com/daggerok/streaming-file-server/releases/download/4.3.3/application.cmd

@rem start
application.cmd start path\to\file-storage

@rem stop
application.cmd stop

@rem cleanup
application.cmd clean path\to\file-storage
```

*note: tested on windows 10 with docker installed locally*

binaries: `which`, `wget`, `docker-compose`, `taskkill`, `mkdir` and of course java (binaries: `java` and `jps`) are required

### with h2 in-memory database

#### manual setup

```bash
wget https://github.com/daggerok/streaming-file-server/releases/download/4.3.3/file-items-service-4.3.3.jar
wget https://github.com/daggerok/streaming-file-server/releases/download/4.3.3/file-server-4.3.3.jar

bash file-items-service-4.3.3.jar --spring.profiles.active=db-h2
bash file-server-4.3.3.jar --app.upload.path=./path/to/file-storage
```

#### or for simplicity use special h2 automation shell-script

```bash
# bash shell script
wget https://github.com/daggerok/streaming-file-server/releases/download/4.3.3/application-h2.bash

# start
bash application-h2.bash start ./path/to/file-storage

# stop
bash application-h2.bash stop

# cleanup
bash application-h2.bash clean ./path/to/file-storage
```

#### h2 automation for windows

```cmd
@rem cmd script
wget https://github.com/daggerok/streaming-file-server/releases/download/4.3.3/application-h2.cmd

@rem start
application-h2.cmd start path\to\file-storage

@rem stop
application-h2.cmd stop

@rem cleanup
application-h2.cmd clean path\to\file-storage
```

*note: tested on windows 10*

binaries: `which`, `del`, `wget`, `taskkill`, `mkdir` and of course `java`, `jps` are required

enjoy :)
