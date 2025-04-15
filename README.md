cd ~/Downloads

tar -xvzf apache-hive-4.0.1-bin.tar.gz

sudo mv apache-hive-4.0.1-bin /usr/local/hive

nano ~/.bashrc

export HIVE_HOME=/usr/local/hive

export PATH=$PATH:$HIVE_HOME/bin

source ~/.bashrc

schematool -initSchema -dbType derby

hive

sudo nano /usr/local/hadoop/etc/hadoop/core-site.xml

<property>
  <name>hadoop.proxyuser.abi.hosts</name>
  <value>*</value>
</property>

<property>
  <name>hadoop.proxyuser.abi.groups</name>
  <value>*</value>
</property>

stop-dfs.sh

start-dfs.sh

hdfs dfs -mkdir -p /user/hive/warehouse

hdfs dfs -chmod -R 777 /user/hive/warehouse

hiveserver2

beeline -u jdbc:hive2://localhost:10000

CREATE DATABASE studentdb;
USE studentdb;

CREATE TABLE students (
  id INT,
  name STRING,
  age INT
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
STORED AS TEXTFILE;

nano ~/students.csv

1,Alice,20
2,Bob,21
3,Charlie,22

LOAD DATA LOCAL INPATH '/home/abi/students.csv' INTO TABLE students;

SELECT * FROM students;

