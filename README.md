# keepalived

Keepalived is facilities for load balancing and high-availability to Linux system and Linux based infrastructures. Load balancing framework relies on well-known and widely used Linux Virtual Server (IPVS) kernel module providing Layer4 load balancing.

Please create keepalived.conf first

CMD using Docker run:-

docker run -d --rm --name keepalived --net=host --cap-add=NET_ADMIN --cap-add=NET_BROADCAST --cap-add=NET_RAW --privileged -v ./keepalived.conf:/etc/keepalived/keepalived.conf amundead/keepalived:bookworm-slim-2.3.2

