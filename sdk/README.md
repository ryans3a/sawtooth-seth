
The Next Generation Tutorial
========

This tutorial walks through the process of starting the prototype validator and
3 different intkey transaction processors. Also there are two clients to
generate intkey transactions that can be loaded to the transaction processors.

Tng Branch
================

Make sure you are running on the latest version of the tng branch:

```
   % cd project/sawtooth-core
   % git fetch upstream
   % git checkout upstream/tng
```

Environment Startup
===================

In order to start the vagrant VM, change the current working directory to
sawtooth-core/tools. If don't you have a vagrant VM running, run:

```
   % cd sawtooth-core/tools
   % vagrant up
   % vagrant ssh
```

After running vagrant ssh you will need to install grpc in the VM:

```
   % cd /project/sawtooth-core/tools/plugins
   % sudo ./install_grpc.sh
```

Now that grpc is installed, the protobuf files need to be generated. The
protogen script generates python classes based on the proto files found in the
protos directory and writes them into
sawtooth-core/sdk/python/sawtooth_protobuf and
sawtooth-core/validator/sawtooth_validator/protobuf:

```
   % cd /project/sawtooth-core
   % ./bin/protogen
```

Python Intkey Transaction Processors
===================

To run the Intkey Transaction Processor, we need to generate a intkey
transactions file. Run the following command to generate the file
batches.intkey:

```
   % ./bin/intkey generate
```

Before we can load the transactions we need to start a validator and a
transaction processor. Run the following to start the validator:

```
   % ./bin/validator
```

In a new terminal, run the following to start the transaction processor:

```
   %cd /project/sawtooth-core
   % ./bin/tp_intkey
```

Finally, it is time to load the transactions. In a new terminal, run:

```
   %cd /project/sawtooth-core
   % ./bin/intkey load
```

Java Intkey Transaction Processors
===================

First, java and maven needs to be installed:

```
   % cd /project/sawtooth-core/tools/plugins
   % sudo ./install_jdk.sh
```

Next, the java sdk and java Intkey Transaction Processor needs to be built.
This is done by using maven and a pom.xml file. The sdk pom.xml file is located
at sawtooth-core/sdk/java and and the intkey pom.xml file is located at
sawtooth-core/sdk/examples/intkey_java. To do this, run the following scripts::

```
   % cd /project/sawtooth-core
   % ./bin/build_java_sdk
   % ./bin/build_java_intkey
```

The transactions files need to be generated. Run the following command to
generate the file batches.intkey:

```
   % ./bin/intkey generate
```

Before we can load the transactions we need to start a validator and a
transaction processor. Run the following to start the validator:

```
   % ./bin/validator
```

In a new terminal, run the following to start the transaction processor:

```
   %cd /project/sawtooth-core
   % ./bin/run_java_intkey
```

Finally, it is time to load the transactions. In a new terminal, run:

```
   %cd /project/sawtooth-core
   % ./bin/intkey load
```

JVM-SC Intkey Transaction Processors
===================

First, java and maven needs to be installed if not already.

```
   % cd /project/sawtooth-core/tools/plugins
   % sudo ./install_jdk.sh
```

Next, the java sdk and jvm-sc Transaction Processor needs to be built.
This is done by using maven and pom.xml files. The sdk pom.xml file is located
at sawtooth-core/sdk/java and and the intkey pom.xml file is located at
sawtooth-core/sdk/examples/intkey_jvm_sc. To do this, run the following scripts:

```
   % cd /project/sawtooth-core
   % ./bin/build_java_sdk
   % ./bin/build_jvm_sc
```

Next the IntKey Smart Contract needs be compiled so the class file exists:

```
   % cd /project/sawtooth-core/sdk/examples/intkey_jvm_sc
   % javac Intkey.java
```

The transactions files need to generated. Run the following command to
generate the file batches_jvm.intkey:

```
   % cd /project/sawtooth-core
   % ./bin/intkey_jvm generate
```

Before we can load the transactions we need to start a validator and a
transaction processor. Run the following to start the validator:

```
   % ./bin/validator
```

In a new terminal, run the following to start the transaction processor:

```
   % cd /project/sawtooth-core
   % ./bin/run_jvm_sc
```

Finally, it is time to load the transactions. In a new terminal

```
   % cd /project/sawtooth-core
   % ./bin/intkey_java load
```