# SingleCellExplorer: web applicaton for exploring single cell datasets
#  with Integration of Python Notebook
####### The software requires Python 3.5 or above Ubuntu 18.04 (and above) 

sudo apt-get update

sudo apt install python3

sudo apt install python3-pip

pip3 install Django

### install and start mongodb

curl -O https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-3.6.12.tgz

tar -zxvf mongodb-linux-x86_64-3.6.12.tgz

mkdir -p mongodb

mv mongodb-linux-x86_64-3.6.12/ mongodb

### create database 

mkdir mongodb/scdb

mkdir mongodb/log

sudo mongodb/mongodb-linux-x86_64-3.6.12/bin/mongod --dbpath "mongodb/scdb" --nssize 2000 --port 27017 --fork --logpath "mongodb/log/scdb.log"

### restore database using example mongodb files

mkdir dumpfiles

unzip scDB.zip

mv scDB dumpfiles

mongodb/mongodb-linux-x86_64-3.6.12/bin/mongorestore dumpfiles

### connect mongodb

mongodb/mongodb-linux-x86_64-3.6.12/bin/mongo

### install dependencies for application

pip3 install -r req.txt
## optional
pip install --user phate`

### start django web application

cd singleCellApp

gunicorn singleCell.wsgi:application -b 0.0.0.0:8000

