FROM docker.io/tmdcio/alpine:3.24-curated.v1 as osdeps

RUN apk add --no-cache ca-certificates

ARG BINARY=prometheus-nats-exporter

FROM docker.io/tmdcio/rfubu:24.04-scratch-curated.v3

COPY ${BINARY} /${BINARY}

COPY --from=osdeps /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/

EXPOSE 7777

ENTRYPOINT ["/prometheus-nats-exporter"]
CMD ["--help"]
