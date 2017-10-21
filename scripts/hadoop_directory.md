[← back to *Main Page*](https://github.com/LogSigma/Hadoop/blob/master/README.md)


# Hadoop Directory Management
```sh
/usr/local/hadoop        # Share Hadoop Core settings among the nodes
/usr/local/hadoop_eco    # Share Hadoop Ecosystem settings
/usr/local/hadoop_dat    # Separate each Node data against push_all.sh
/usr/local/hadoop_log    # Separate each Node logs against push_all.sh
/usr/local/hadoop_var    # Separate each Node PIDs or some variables against push_all.sh
```

## Hadoop floer Setting
```sh
sudo chown -R [usrname]:[usrname] /usr/local/hadoop_eco
sudo chown -R [usrname]:[usrname] /usr/local/hadoop_dat
sudo chown -R [usrname]:[usrname] /usr/local/hadoop_log
sudo chown -R [usrname]:[usrname] /usr/local/hadoop_var
```

[← back to *Main Page*](https://github.com/LogSigma/Hadoop/blob/master/README.md)
