# SOCKS5 Server for Telegram

This Ansible playbook initializes a SOCKS5 server on any Ubuntu 16.04 machine.
For anonymous server, run:

    ansible-playbook -i '12.34.56.78,' playbook.yml

Note that the IP address should have a trailing comma. When you want to specify
user name and password, add relevant tags:

    ansible-playbook -i '12.34.56.78,' playbook.yml -e user=thatsme password=q1w2e3r4

Finally, you can change port from the default 1080 by using `tport` variable:

    ansible-playbook -i '12.34.56.78,' playbook.yml -e tport=1089

## Testing

Run this command to test a server without auth:

    curl -v -x socks5://12.34.56.78:1080 http://t.me

And with auth:

    curl -v -x socks5://thatsme:q1w2e3r4@12.34.56.78:1080 http://t.me

Try querying google.com to see that only telegram endpoints are allowed.

## Author

This playbook was written by Ilya Zverev and published under WTFPL.

## See Also

These articles and code were used to make this playbook (mostly in Russian):

* [Installing Dante on Ubuntu 16](https://weril.me/index.php/2018/04/13/installation_and_using_dante_as_socks5_proxy_on_ubuntu_16/) by Petr Redkin
* [How to deploy own socks5 server](https://robot-review.ru/%D0%B3%D0%B0%D0%B9%D0%B4-%D0%BA%D0%B0%D0%BA-%D0%BF%D0%BE%D0%B4%D0%BD%D1%8F%D1%82%D1%8C-%D1%81%D0%B2%D0%BE%D0%B9-socks5-%D1%81%D0%B5%D1%80%D0%B2%D0%B5%D1%80-%D0%B4%D0%BB%D1%8F-telegram-e29761a68560) by Andrey Viktorov
* [Setting up a Telegram proxy server for 2.94€](https://ubuntuclub.org/nastroika-lichnogho-proxy-servera-dlia-telegram-za-2-94-euro/) © Ubuntu Club
* [Dockerized socks5 proxy for Telegram](https://github.com/schors/tgdante2) by Phil Kulin
* [Telegram calls via Dante not working](https://stackoverflow.com/questions/49855516/telegram-calls-via-dante-socks5-proxy-server-not-working), answer by Kostya Esmukov
