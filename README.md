# Mini-Project-1

The objective of this mini project is to get familiar with setting up and programming the Hadoop system

## Requirements
* Hadoop 
* Virtual machines
* [Putty](http://www.putty.org/)  - An SSH client 
* Docker

## Installation

## Running the Hadoop program

2021-03-04 

### Part1


1. Configure /etc/hosts on every node

````
ubuntu@cc-project-22:~/hadoop$vi /etc/hosts
   Type these:
   10.11.10.21 CC-project-22
   10.11.10.59 CC-project-23
   10.11.13.209 CC-project-24
````
2. Configure the cluster setting on every node

````
ubuntu@cc-project-22:~/hadoop$vi /etc/workers
ubuntu@cc-project-22:~/hadoop$vi /etc/core-site.xml
ubuntu@cc-project-22:~/hadoop$vi /etc/hdfs-site.xml
ubuntu@cc-project-22:~/hadoop$vi /etc/yarn-site.xml
ubuntu@cc-project-22:~/hadoop$vi /etc/mapred-site.xml
   
   
Insert parts provided in each file above
````
3. Format the name node on master 
````
ubuntu@cc-project-22:~/hadoop$hadoop namenode -format
````
4. Start HDFS, YARN, and Job History Server
````
ubuntu@cc-project-22:~/hadoop$sbin/start-dfs.sh
ubuntu@cc-project-22:~/hadoop$sbin/start-yarn.sh
ubuntu@cc-project-22:~/hadoop$sbin/mr-jobhistory-daemon.sh --config etc/hadoop/ start historyserver
````
5. Moniter the services as below
````
ubuntu@cc-project-22:~/hadoop$jps
10261 Jps
2521 ResourceManageer
3977 NameNode
3115 JobHistoryServ:wq\\er
4283 SecondaryNameNode
2733 NodeManager
ubuntu@cc-project-22:~/hadoop$ssh cc-project-23
ubuntu@cc-project-23:~$jps
22038 NodeManager
21847 DataNode 
11789 Jps
ubuntu@cc-project-22:~/hadoop$ssh cc-project-24
ubuntu@cc-project-24:~$jps
10073 Jus
20299 NodeManager
20109 DataNode
````
6. Test HDFS
````
ubuntu@cc-project-22:~/hadoop$bin/hdfs dfs -mkdir input
ubuntu@cc-project-22:~/hadoop$bin/hdfs dfs put etc/hadoop/*.xml input
ubuntu@cc-project-22:~/hadoop$bin/hdfs dfs -ls input
````
7. Test with wordcount program, input file

````
ubuntu@cc-project-22:~/hadoop$bin/hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-3.2.1.jar
wordcount input output2

ubuntu@cc-project-22:~/hadoop$bin/hdfs dfs -cat output2/*
````

## License 

This project is licensed under the MIT License - see the [MIT License](https://opensource.org/licenses/MIT) for details.
