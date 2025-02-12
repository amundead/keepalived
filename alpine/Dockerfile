# Use the Alpine Linux base image
FROM alpine:latest

# Update the package list and install keepalived
RUN apk update && apk add --no-cache keepalived

# Start keepalived when the container launches
CMD ["keepalived", "-n", "-D", "/etc/keepalived/keepalived.conf", "--log-console"]