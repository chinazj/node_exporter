ARG ARCH="arm64"
ARG OS="linux"

FROM golang:1.13
RUN mkdir -p /go/src/github.com/prometheus/node_exporter
WORKDIR /go/src/github.com/prometheus/node_exporter
RUN chmod -R 777 /go
COPY / /go/src/github.com/prometheus/node_exporter
COPY /build/arm64/Makefile /go/src/github.com/prometheus/node_exporter/Makefile
COPY /build/arm64/Makefile.common /go/src/github.com/prometheus/node_exporter/Makefile.common
RUN make build 

ARG ARCH="arm64"
ARG OS="linux"
FROM quay.io/prometheus/busybox-${OS}-${ARCH}:glibc
LABEL maintainer="The Prometheus Authors <prometheus-developers@googlegroups.com>"
COPY --from=0 /go/src/github.com/prometheus/node_exporter/node_exporter /bin/node_exporter
EXPOSE      9100
USER        nobody
ENTRYPOINT  [ "/bin/node_exporter" ]
