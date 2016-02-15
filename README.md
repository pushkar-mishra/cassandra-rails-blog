# cassandra-rails-blog

Open new terminal window

Download Cassandra

$ cd
$ wget http://archive.apache.org/dist/cassandra/2.2.0/apache-cassandra-2.2.0-bin.tar.gz
Installing Cassandra

$ cd
$ gzip -dc apache-cassandra-2.2.0-bin.tar.gz | tar xf -
Update .profile with the following lines:

# set environment variables for Cassandra.
export CASSANDRA_VERSION=2.2.0
export CASSANDRA_HOME=${HOME}/apache-cassandra-${CASSANDRA_VERSION}
export PATH=${CASSANDRA_HOME}/bin:${PATH}
Then execute the following command within the terminal:

$ . ~/.profile
Start Cassandra

$ cassandra -f
