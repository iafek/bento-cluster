# FROM kijiproject/bento-cluster-base:cdh5
FROM cdhbase:latest
MAINTAINER Itamar Afek <iafek@salesforce.com>

RUN yum-config-manager --add-repo http://archive.cloudera.com/cdh5/redhat/6/x86_64/cdh/5.2.1/

RUN yum install -y --nogpgcheck \
  zookeeper-server \
  hadoop-hdfs-namenode \
  hadoop-hdfs-datanode \
  hadoop-yarn-resourcemanager \
  hadoop-yarn-nodemanager \
  hadoop-yarn-proxyserver \
  hadoop-mapreduce \
  hadoop-mapreduce-historyserver \
  hbase-master \
  hbase-regionserver
#  oozie \
#  hive \
#  hue

# Install Hadoop configuration
RUN alternatives --verbose --install /etc/hadoop/conf hadoop-conf /etc/hadoop/conf.bento 50 && alternatives --set hadoop-conf /etc/hadoop/conf.bento

# Install ZooKeeper configuration
RUN alternatives --verbose --install /etc/zookeeper/conf zookeeper-conf /etc/zookeeper/conf.bento 50 && alternatives --set zookeeper-conf /etc/zookeeper/conf.bento

# Install HBase configuration
RUN alternatives --verbose --install /etc/hbase/conf hbase-conf /etc/hbase/conf.bento 50 && alternatives --set hbase-conf /etc/hbase/conf.bento

# Install Oozie configuration
#RUN alternatives --verbose --install /etc/oozie/conf oozie-conf /etc/oozie/conf.bento 50
#RUN alternatives --set oozie-conf /etc/oozie/conf.bento

# Install Hive configuration
#RUN alternatives --verbose --install /etc/hive/conf hive-conf /etc/hive/conf.bento 50
#RUN alternatives --set hive-conf /etc/hive/conf.bento

USER root
CMD ["/start"]
