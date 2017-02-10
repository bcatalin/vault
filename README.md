# vault

-------------------------------------------------------------------------
https://www.howtoforge.com/tutorial/install-mongodb-on-ubuntu-16.04/
-------------------------------------------------------------------------

sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927
echo "deb http://repo.mongodb.org/apt/ubuntu "$(lsb_release -sc)"/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list

sudo apt-get update
sudo apt-get install -y mongodb-org
systemctl daemon-reload
systemctl start mongod
systemctl enable mongod
netstat -plntu
------------------------------
mongo     ( one error "export LC_ALL=C; mongo" )
use admin
db.createUser({user:"catalin", pwd:"catalin", roles:[{role:"root", db:"admin"}]})
exit

vim /lib/systemd/system/mongod.service
* add ExecStart=/usr/bin/mongod --quiet --auth --config /etc/mongod.conf (--auth)
systemctl daemon-reload
mongo -u catalin -p catalin --authenticationDatabase admin
>show dbs
