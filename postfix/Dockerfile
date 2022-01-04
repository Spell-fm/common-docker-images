FROM alpine:3.14

ENV TZ Europe/Berlin

RUN apk add --no-cache postfix postfix-mysql postfix-pcre

EXPOSE 25

CMD ["/usr/sbin/postfix","start-fg"]