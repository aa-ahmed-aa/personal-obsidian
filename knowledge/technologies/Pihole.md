docker install : https://github.com/pi-hole/pi-hole/?tab=readme-ov-file#method-3-using-docker-to-deploy-pi-hole


# Caveat
there are so many ways to install pihole here i'm running pihole on the docker image and serving pihole DNS server on port 53 after disabling the default DNS server on ubuntue and giving my personal mini PC a static ip so later i will configure my router to use this DNS server as the default one 

### 1. disable your local DNS server
1.1 give your machine a static ip from the router 
1.2
```bash
sudo systemctl disable systemd-resolved
sudo systemctl stop systemd-resolved
```

### 2. run the docker image of pihole
notice the web interface port on `8019` because the default of pihole is 80 but port 53 is now our machine default DNS server

```bash
docker run -d \
    --name pihole \
    -p 53:53/tcp -p 53:53/udp \
    -p 8019:80 \
    -e TZ="Europe/Tallinn" \
    -v "${PIHOLE_BASE}/etc-pihole:/etc/pihole" \
    -v "${PIHOLE_BASE}/etc-dnsmasq.d:/etc/dnsmasq.d" \
    --dns=127.0.0.1 --dns=1.1.1.1 \
    --restart=unless-stopped \
    --hostname pi.hole \
    -e VIRTUAL_HOST="pi.hole" \
    -e PROXY_LOCATION="pi.hole" \
    -e FTLCONF_LOCAL_IPV4="127.0.0.1" \
    pihole/pihole:latest
```


get the password for the UI `docker logs pihole 2> /dev/null | grep 'password:'`

### 3. configure Router DNS
now we will configure the router primary DNS on our router to filter everything in our network  go to the router configuration and configure the DHCB to use your static machine IP we previously set this will restart the router