# install kafka service

## Download

download here:
https://www.apache.org/dyn/closer.cgi?path=/kafka/1.0.0/kafka_2.11-1.0.0.tgz

for example this:
http://www-eu.apache.org/dist/kafka/1.0.0/kafka_2.11-1.0.0.tgz

## Install as a service:

Zookeeper
```
$ cat > /etc/systemd/system/zookeeper.service
[Unit]
Description=Zookeeper for Kafka

[Service]
Type=simple
User=j0k
ExecStart=/home/j0k/soft/kafka_2.11-1.0.0/bin/zookeeper-server-start.sh /home/j0k/soft/kafka_2.11-1.0.0/config/zookeeper.properties
Restart=on-abort

[Install]
WantedBy=multi-user.target
```

Kafka
```
$ cat >  /etc/systemd/system/kafka.service
[Unit]
Description=Kafka for Data

[Service]
Type=simple
User=j0k
ExecStart=/home/j0k/soft/kafka_2.11-1.0.0/bin/kafka-server-start.sh /home/j0k/soft/kafka_2.11-1.0.0/config/server.properties
Restart=on-abort

[Install]
WantedBy=multi-user.target
```

then run
```
$ systemctl daemon-reload
$ systemctl start zookeeper
$ systemctl start kafka
```

to see logs and quit:
```
$ journalctl -u kafka
```

to watch logs in RT:
```
$ journalctl -u kafka -f
```

[RT] - RealTime

** Thanks to couozu**
