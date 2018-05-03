# Hadoop-Multi-Cluster

INSTRUCTIONS TO RUN THE APPLICATION PROGRAM

1.Create directory /home/ubuntu/inputdata on the namenode and copy all input files into inputdata

2.Create a directory /user in HDFS:

cd /usr/local/hadoop bin/hdfs dfs -mkdir /user

3.Copy the inputdata folder to HDFS:

cd /usr/local/hadoop/ bin/hdfs dfs -put '/home/ubuntu/inputdata' /user/

4.Create directory /home/ubuntu/wordcountf on namenode and copy the java application program, WordCount.java into wordcountf

5.Compile the java application program:

cd /home/ubuntu/wordcountf javac -classpath $HADOOP_HOME/share/hadoop/common/hadoop-common-2.7.2.jar:$HADOOP_HOME/share/hadoop/mapreduce/hadoop-mapreduce-client-core-2.7.2.jar:$HADOOP_HOME/share/hadoop/common/lib/commons-cli-1.2.jar -d ./ *.java

6.Create a folder wordcountc inside wordcountf and move all class files into wordcountc

7.Create jar file by executing the command below:

cd /home/ubuntu/wordcountf jar -cvf wordcountj.jar -C wordcountc .

This will create the jar file named wordcountj.jar

8.Run the application program

cd /usr/local/hadoop bin/hadoop jar ~/wordcountf/wordcountj.jar WordCount /user/inputdata/ output2

9.Output is genetated inside two folders: output1(count of keywords in each state) and output2(top 3 states for each keyword)

cd /usr/local/hadoop hdfs dfs -cat /user/ubuntu/output1/part-r-00000 hdfs dfs -cat /user/ubuntu/output2/part-r-00000
