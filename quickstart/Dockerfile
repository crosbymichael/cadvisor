FROM ubuntu:14.04
MAINTAINER kyurtsever@google.com dengnan@google.com vmarmol@google.com

# Get the lmctfy dependencies.
RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y --force-yes pkg-config libprotobuf8 libapparmor1
ADD http://storage.googleapis.com/cadvisor-bin/lmctfy/libre2.so.0.0.0 /usr/lib/libre2.so.0

# Get the lcmtfy and cAdvisor binaries.
ADD http://storage.googleapis.com/cadvisor-bin/lmctfy/lmctfy /usr/bin/lmctfy
ADD http://storage.googleapis.com/cadvisor-bin/cadvisor /usr/bin/cadvisor
RUN chmod +x /usr/bin/lmctfy && chmod +x /usr/bin/cadvisor

# Clean up apt and other locations
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 8080
ENTRYPOINT ["/usr/bin/cadvisor"]
