# Cowrie-Ansible

Requirements

	User with SUDO 

	SSH On a NON standard port

	Create redirect from port 2222 --> 22 (iptables)



Usage

Edit sites.yaml and replace $USER with your user that has access to sudo.



OverView

Config values are located in roles/cowrie/defaults/main.yaml

Update, install packages & Pip install 

Set up cowrie users with home directory located in /opt/cowrie.

Clone down https://github.com/bizarrechaos/cowrie into /opt/cowrie/cowrie

Setup VirtualEnv in /opt/cowrie/cowrie/env for honeypot & install packages 

Create /etc/init.d/cowrie so this can be call via service ie: service cowrie start:restart:stop 

Start Cowrie port 2222

Create alias in $USER .backrc, LOG to tail -f /opt/cowrie/cowrie/log/cowrie.log

Create alias in $USER .backrc, COWRIE='sudo su - cowrie'

Create alias in $USER .backrc, 22REDIRECT = iptables NAT rule to redirect port 2222 to 2222

	sudo iptables -t nat -A PREROUTING -p tcp --dport 22 -j REDIRECT --to-ports 2222