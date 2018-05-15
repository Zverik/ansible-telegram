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
