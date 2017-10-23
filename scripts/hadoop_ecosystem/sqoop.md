[← back to *Main Page*](https://github.com/LogSigma/Hadoop/blob/master/README.md)

# Sqoop Install

## Sqoop Download
```sh
cd /usr/local/hadoop_eco
```
```sh
wget http://archive.apache.org/dist/sqoop/1.99.7/sqoop-1.99.7-bin-hadoop200.tar.gz
tar xzf sqoop-1.99.7-bin-hadoop200.tar.gz
mv sqoop-1.99.7-bin-hadoop200.tar.gz sqoop
```

## ```.bashrc``` Update
```sh
vi ~/.bashrc
```
```sh
export SQOOP_HOME=/usr/local/hadoop_eco/sqoop
export PATH=$PATH:$SQOOP_HOME/bin
export SQOOP_CONF_DIR=$SQOOP_HOME/conf
export SQOOP_CLASS_PATH=$SQOOP_CONF_DIR
export SQOOP_SERVER_EXTRA_LIB=/usr/local/hadoop_eco/sqoop/libs
```
```sh
source ~/.bashrc
```

## Confiture ```core-site.xml``` Update
```sh
cd /usr/local/hadoop/ect/hadoop
vi core-site.xml
```
```xml
<configuration>
        <property>
                <name>hadoop.proxyuser.master1.hosts</name>
                <value>*</value>
        </property>
        <property>
                <name>hadoop.proxyuser.master1.groups</name>
                <value>*</value>
        </property>
</configuration>
```

## MySQL JDBC Dirver Download
```sh
cd $SQOOP_HOME/libs
```
```sh
wget http://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.28.tar.gz
tar zxf mysql-connector-java-5.1.28.tar.gz
```

[← back to *Main Page*](https://github.com/LogSigma/Hadoop/blob/master/README.md)
