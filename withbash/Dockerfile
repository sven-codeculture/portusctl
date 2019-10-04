FROM golang:alpine

MAINTAINER codeculture <info@codeculture.de>

WORKDIR $GOPATH/src/portusctl


RUN apk add --update --no-cache git openssh-client bash musl-dev build-base && \
    git clone https://github.com/openSUSE/portusctl $GOPATH/src/portusctl && \
    go get github.com/mssola/capture && \
    go get gopkg.in/urfave/cli.v1 && \
    # We need to remove buildmode pie since it does not work with CGO which is required for static bineries
    sed -i "s/-buildmode=pie//" ./Makefile && \
    CGO_ENABLED=0 GOOS=linux make install BUILD_FLAGS="-a"

FROM alpine
MAINTAINER codeculture <info@codeculture.de>

RUN apk add --update --no-cache bash jq
COPY --from=0 /go/bin/portusctl /bin/portusctl

ENTRYPOINT ["/bin/bash"]
