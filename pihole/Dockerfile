FROM pihole/pihole:4.3.2-1

WORKDIR /usr/src

RUN sed -i '/$AUTHORIZED_HOSTNAMES = array(/ a "balena-devices.com",' /var/www/html/admin/scripts/pi-hole/php/auth.php

# https://serverfault.com/a/817791
# force dnsmasq to really bind only the interfaces it is listening on
# otherwise dnsmasq will fail to start since balena is using 53 on some interfaces
RUN echo "bind-interfaces" >> /etc/dnsmasq.conf

#RUN curl -fsSL https://github.com/jpmck/PADD/archive/v3.0.2.tar.gz | tar xz --strip-components 1 \
#	&& chmod +x padd.sh

# use wally3k's ticked list from https://firebog.net/
RUN curl -sSL https://v.firebog.net/hosts/lists.php?type=tick -o /etc/pihole/adlists.list
