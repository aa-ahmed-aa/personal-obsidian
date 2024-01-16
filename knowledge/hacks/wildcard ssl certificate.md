there is a certbot plugins but in this note i will go throw installing a wildcard certificate with renewal on for [godaddy which is a manual plugin](https://github.com/miigotu/certbot-dns-godaddy)

1. ssh into your server
2. make sure you have certbot and [all required plugins installed](https://certbot.eff.org/instructions?ws=nginx&os=ubuntufocal&tab=wildcard)
3. create [godaddy api token](https://developer.godaddy.com/keys) and store it in `/var/lib/letsencrypt/godaddy_credentials.ini`
4. for dns-godaddy plugin we will run it using docker mounting container volums to our local `/etc/letsencrypt`,  so we will :- 
5. run `docker pull miigotu/certbot-dns-godaddy`
6. then run ```docker run --rm \
	  -v /var/lib/letsencrypt:/var/lib/letsencrypt \
	  -v /etc/letsencrypt:/etc/letsencrypt \
	  --cap-drop=all \
	  miigotu/certbot-dns-godaddy certbot certonly \
	    --authenticator dns-godaddy \
	    --dns-godaddy-propagation-seconds 900 \
	    --dns-godaddy-credentials /var/lib/letsencrypt/godaddy_credentials.ini \
	    --keep-until-expiring --non-interactive --expand \
	    --server https://acme-v02.api.letsencrypt.org/directory \
	    --agree-tos --email "<EMAIL>" \
	    -d <MAIN_DOMAIN> -d '*.<MAIN_DOMAIN>'    
7. make sure to fix [this issue](https://github.com/miigotu/certbot-dns-godaddy?tab=readme-ov-file#exception) in the plugin after the certificate is generated