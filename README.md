## Cloud Computing Mini Project 1

## Part 1: Setting up Hadoop: (50 points)

## Group Members:

* Anthony Harris: AGH41@pitt.edu
* Haodong Xu: HAX31@pitt.edu
* Jane Sunyoung Lee:   SUJ20@pitt.edu
* Jose Zindia: jdz18@pitt.edu

NB: See Attached problem1_code file for source code 


## Requirements
* Hadoop 
* Virtual machines
* [Putty](http://www.putty.org/)  - An SSH client 
* Docker

## Running the Hadoop program

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

## Cloud Computing Mini Project 1

## Part 3: Developing a Hadoop program (25 points)

## Group Members:

* Anthony Harris: AGH41@pitt.edu
* Haodong Xu: HAX31@pitt.edu
* Jane Sunyoung Lee:   SUJ20@pitt.edu
* Jose Zindia: jdz18@pitt.edu

NB: See Attached problem1_code file for source code 
   
  ``` 
  Change your own path in WordcountDriver class.
  Run main() in WordcountDriver class.
  Put your data in the input file.
  Input n on the consle and get output in part-r-00000 in the output file.
````
