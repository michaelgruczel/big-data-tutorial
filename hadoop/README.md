# hadoop basics

back https://github.com/michaelgruczel/big-data-tutorial

## Understanding the concepts behind hadoop

**Map reduce**

One of the most famous parts of the hadoop ecosystem is the map-reduce algorithm-
Let's say You have a list of data entries. Every entry contains a car id, the temparture of the engine, the car type, a timestamp and other information. You want to know how how an engine of a car can be in real life scenarios, means you want to have the highest temperature for each car type. 

raw data:

    id123,110,typeA,2017-11-11,...
    id234,102,typeB,2017-11-12,...
    id345,105,typeA,2017-10-10,...
    ...

The map step reduces the dataentries to the information we realy need for our calculation

mapped data:

    typeA,110
    typeB,102
    typeA,105

Hadoop adds an additional step automatically. It sorts and shuffles the data, so we get

sorted and shuffled 

    typeA, (110,105)
    typeB, (102)

The reduce taks now reduces the dataset to the result we are interested in:

reduced:

    typeA,110
    typeB,102

That seems to be a complex way to solve things for just a simple calculation, but the advantage is that we can run the calculation in parallel, that's where HDFS comes into play.

**HDFS**

Hadoop Distributed File System splits the dataset into subsets and distributes the chunks over a cluster (subsets on several nodes).
That means a calculation is not done on a single node, instead the calculation can be done in parallel, which gives map reduce it's power and reliant storage of petabytes of data is doable on commodity hardware.
In order to make this possible new data can be appended to the end of files, bur files cannot be edited and files are sliced into blocks (128 MB by default)

**YARN** 

A map reduce job is splitted into map tasks and reduce tasks. The tasks are scheduled by YARN to the different nodes. The data is splitted to the different nodes as well, thanks to HDFS.
With a smart distribution of tasks and data, the calculation of massive data can be highly parallized.  

![1](https://github.com/michaelgruczel/big-data-tutorial/raw/master/hadoop/mapreduce-1.png "distribution")
![2](https://github.com/adam-p/markdown-here/raw/master/src/common/images/hadoop-basic.png "hadoop basic")

## understand the infrastructure concepts behind hadoop

A HDFS cluster consists of Namenodes (master) and Datanodes (workers).
The namenode holds filesystem metadata in memory and manages the namespace and the filesystem tree.
The data is persistet ein files and loaded at restart of the node.
The master can run in HA mode, means a primary and a secodary, the failover is normally managed by ZooKeeper.

In this repositiy you will find a a vagrant description, creating a small hadoop cluster.
The setup looks like this:

![3](https://github.com/adam-p/markdown-here/raw/master/src/common/images/hadoop-vagrant.png "vagrant setup")

## let's play with hadoop

You need 2 shells. Open the 2 shells and navigate into the folder with this README file.
In one shell we are building our Java programs, in the second we will work in the hadoop cluster.

So let us create a local hadoop cluster using vagrant and log into one slave:

    # shell 2
    vagrant up
    vagrant ssh hadoopslave1

now let's play with the installation:

    # shell 2
    # let's copy a file to hdfs and back to local filesystem
    sudo su - mapred
    hadoop fs -ls /
    hadoop fs -mkdir /testfolder
    hadoop fs -ls /
    hadoop fs -copyFromLocal testinputfile.txt hdfs://localhost/testfolder/testinputfileinhdfs.txt
    hadoop fs -ls /
    hadoop fs -copyToLocal hdfs://localhost/testfolder/testinputfileinhdfs.txt testinputfileisback.txt 
    
Hadoop is written in Java and offers an API which can be used for implementing own programs in several languages.
Let us run sonme java programs.

In this folder is a gradle project you can use to build several java programs.
You can open it with your favorite editor to change code.
You have to change the main class in the build.gradle file to the one you want to test in hadoop.
Then you can build the jar (containing all the code from the project, but using your main class as default).
So lets start with a simple example. You will find a reader class in the project:


##################################################################################

not yet tested:

<PRE>

public class TestReader {
  public static void main(String[] args) throws Exception {
    FileSystem fs = FileSystem.get(URI.create(args[0]), new Configuration());
    InputStream in = null;
    try {
      in = fs.open(new Path(args[0]));
      IOUtils.copyBytes(in, System.out, 4096, false);
    } finaly {
      IOUtiles.closeStream(in);
    }
  } 
}

</PRE>   

This progran just reads from the hadoop filesystem. 
Let's build and run it.

    # shell 1
    gradlew build

and run it

    TODO    
    java -jar sharedfoder/.../xxx.jar hdfs://localhost/testfolder/testinputfileinhdfs.txt

This program reads data form hadoop, but it was not a hadoop program, So let us write a simple map reduce program:

TODO

