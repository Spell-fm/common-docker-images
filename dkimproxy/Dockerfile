FROM alpine:3.14

RUN apk add --no-cache dkimproxy

ENTRYPOINT ["/usr/sbin/dkimproxy.out"]

CMD ["--conf_file=/etc/dkimproxy/dkimproxy_out.conf"]