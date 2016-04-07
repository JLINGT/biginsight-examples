#### Overview

This example retrieves data from a dashDB database and saves it to HDFS.  This example is run by gradle and using ssh:

 1. create a temporary folder in the user's home folder on the cluster
 1. download db2 jdbc jar files from the cluster to the local build environment
 2. upload db2 jdbc jar files and spark script from the local build environment to the temporary user's folder on the cluster
 3. create a hdfs folder for storing the data imported from dashdb
 4. execute pyspark to import the data and copy it to hdfs
 5. cat the file created on hdfs to view its output
 6. cleanup by removing the hdfs folder and the temporary user's folder on the cluster

Take a look at the [build.gradle](./build.gradle) file, starting with the Example task defintion `task('Example') { ... }`  and then move on to the spark script [importfromdashdb.py](./importfromdashdb.py) to see exactly what is being done.

*********************************************************************
#### Instructions

Make sure your connection.properties file has values set to point to the dashDB account:

```
dashdb_pull_jdbc_url:jdbc:db2://changeme:50001/BLUDB:user=changeme;password=changeme;sslConnection=true;
```

Run this example by changing into the current directory then executing:

- on *nix using:

```
../../gradlew Example
```

- on Windows using:

```
../../gradlew.bat Example
```

*********************************************************************

Note: you can run this script from the top level project folder using the gradle `-p` argument:

```
./gradlew -p examples/DashDBPullWithSpark Example
```
*********************************************************************