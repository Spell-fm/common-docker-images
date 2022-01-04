# SQLgrey
# http://sqlgrey.sourceforge.net/

FROM alpine:3.14

LABEL org.thenetcircle.image.authors="sysadmins@thenetcircle.com"

# Install build essentials
RUN apk add --no-cache --virtual .build-deps make

# Install runtime depencencies, perl and required perl modules
RUN apk add perl perl-net-server perl-io-multiplex perl-dbi perl-dbd-mysql

# Decompress and Make install
# https://cfhcable.dl.sourceforge.net/project/sqlgrey/sqlgrey-1.8%20%28stable%29/sqlgrey-1.8.0.tar.gz
COPY sqlgrey-1.8.0.tar.gz /tmp/
RUN tar -xzf /tmp/sqlgrey-1.8.0.tar.gz -C /tmp/
WORKDIR /tmp/sqlgrey-1.8.0
RUN cd /tmp/sqlgrey-1.8.0 && make install

# Add required user and group
RUN addgroup -S sqlgrey && adduser -g sqlgrey -G sqlgrey -H -D sqlgrey

# Clean up
RUN apk del .build-deps && rm -r /tmp/sqlgrey-1.8.0 && rm /tmp/sqlgrey-1.8.0.tar.gz

ENTRYPOINT [ "/usr/sbin/sqlgrey" ]