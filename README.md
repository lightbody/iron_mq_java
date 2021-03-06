IronMQ Java Client
----------------

Getting Started
===============
There are three ways to get this package.

1. Add it as a Maven dependency, using the repository
   `http://iron-io.github.com/maven/repository`. Your pom.xml will look
   something like:

    ...
    <repositories>
        <repository>
            <id>iron-io-repo</id>
            <name>Iron.io Maven repository on GitHub</name>
            <url>http://iron-io.github.com/maven/repository/</url>
        </repository>
    </repositories>

    <dependencies>
        <!-- IronMQ message queue client -->
        <dependency>
            <groupId>ironmq</groupId>
            <artifactId>ironmq</artifactId>
            <version>0.0.10</version>
            <scope>compile</scope>
        </dependency>
    </dependencies>
    ...

2. [Download the jar](https://github.com/iron-io/iron_mq_java/downloads).

3. Build from source with [Apache Buildr](http://buildr.apache.org):

    buildr package

The .jar file will appear under the target directory.

The Basics
==========
The full API is documented [here](http://iron-io.github.io/iron_mq_java/), but
here are some quick snippets to get you started.

**Initialize** a client and get a queue object:

    Client client = new Client("my project", "my token", Cloud.IronAWSUSEast);
    Queue queue = client.queue("my_queue");

**Push** a message on the queue:

    queue.push("Hello, world!");

**Pop** a message off the queue:

    Message msg = queue.get();

When you pop/get a message from the queue, it will *not* be deleted. It will
eventually go back onto the queue after a timeout if you don't delete it. (The
default timeout is 60 seconds.)

**Delete** a message from the queue:

    queue.deleteMessage(msg);
