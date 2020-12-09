# dockerfile start

## An example Dockerfile for install git on ubuntu

```Dockerfile
FROM ubuntu:latest
MAINTAINER "qiaokeke.top"
RUN apt-get install -y git
ENTRYPOINT ["git"]
```
