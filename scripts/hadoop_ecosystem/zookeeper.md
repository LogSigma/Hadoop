[← back to *Main Page*](https://github.com/logsigma/Hadoop/blob/master/Readme.md)

# Zookeeper Install

## Zookeeper Download
```sh
cd /usr/local/hadoop_eco
```
```
wget http://apache.tt.co.kr/zookeeper/stable/zookeeper-3.4.9.tar.gz
tar zxf zookeeper-3.4.9.tar.gz
mv zookeeper-3.4.9.tar.gz zookeeper
```

## Zookeeper Setting
### Create ```dataDir```
```sh
cd /usr/local/hadoop_dat
```
```
mkdir -p zookeeper/data
```

### Create ```zoo.cfg```
```sh
cd /usr/local/hadoop_eco/zookeeper/conf
```
```
cp zoo_sample.cfg zoo.cfg
vi zoo.cfg
```
```
dataDir=/usr/local/hadoop_dat/zookeeper/data

server.1=master1:2888:3888
server.2=master2:2888:3888
server.3=slave1:2888:3888
server.4=slave2:2888:3888
server.5=slave3:2888:3888
autopurge.snapRetainCount=10
autopurge.purgeInterval=12
```

## Copy ```zookeeper``` ```myid``` to Each DateNode
```sh
scp -r /usr/local/hadoop_eco/zookeeper [username]@master2:/usr/local/hadoop_eco
scp -r /usr/local/hadoop_eco/zookeeper [username]@slave1:/usr/local/hadoop_eco
scp -r /usr/local/hadoop_eco/zookeeper [username]@slave2:/usr/local/hadoop_eco
scp -r /usr/local/hadoop_eco/zookeeper [username]@slave3:/usr/local/hadoop_eco
```
```sh
scp -r /usr/local/hadoop_dat/zookeeper/data [username]@master2:/usr/local/hadoop_dat/zookeeper
scp -r /usr/local/hadoop_dat/zookeeper/data [username]@slave1:/usr/local/hadoop_dat/zookeeper
scp -r /usr/local/hadoop_dat/zookeeper/data [username]@slave2:/usr/local/hadoop_dat/zookeeper
scp -r /usr/local/hadoop_dat/zookeeper/data [username]@slave3:/usr/local/hadoop_dat/zookeeper
```
```sh
echo 1 > /usr/local/hadoop_dat/zookeeper/data/myid
ssh [username]@master2 "echo 2 > /usr/local/hadoop_dat/zookeeper/data/myid"
ssh [username]@slave1 "echo 3 > /usr/local/hadoop_dat/zookeeper/data/myid"
ssh [username]@slave2 "echo 4 > /usr/local/hadoop_dat/zookeeper/data/myid"
ssh [username]@slave3 "echo 5 > /usr/local/hadoop_dat/zookeeper/data/myid"
```

## ```.bashrc``` Update & Cope Each DateNode
```sh
vi ~/.bashrc
```
```sh
export ZOOKEEPER_HOME=/usr/local/hadoop_eco/zookeeper
export ZOOKEEPER_PREFIX=$ZOOKEEPER_HOME
export ZOO_LOG_DIR=/usr/local/hadoop_log/zookeeper/logs
export PATH=$PATH:$ZOOKEEPER_HOME/bin
```
```sh
sudo scp -r ~/.bashrc [username]@master2:~/.bashrc
sudo scp -r ~/.bashrc [username]@slave1:~/.bashrc
sudo scp -r ~/.bashrc [username]@slave2:~/.bashrc
sudo scp -r ~/.bashrc [username]@slave3:~/.bashrc
```
```sh
source ~/.bashrc
ssh [username]@master2 "source ~/.bashrc"
ssh [username]@slave1 "source ~/.bashrc"
ssh [username]@slave2 "source ~/.bashrc"
ssh [username]@slave3 "source ~/.bashrc"
```

## Start Zookeeper
```sh
zkServer.sh start
ssh [username]@master2 "zkServer.sh start"
ssh [username]@slave1 "zkServer.sh start"
ssh [username]@slave2 "zkServer.sh start"
ssh [username]@slave3 "zkServer.sh start"
```

## Check Zookeeper
```sh
jps
```
* ```QuorumPeerMain```

## Stop Zookeeper
```sh
zkServer.sh stop
```

[← back to *Main Page*](https://github.com/zyskuuk/Hadoop/blob/master/Readme.md)
