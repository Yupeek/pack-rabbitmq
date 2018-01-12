pack-rabbitmq
#############

Shinken configuration pack for rabbitmq status check.

it use the http backend of rabbitmq to query state of server.

Installation
============

install required perl dependency

.. code::

	perl -MCPAN -e "CPAN::Shell->notest('install', 'JSON')"
	perl -MCPAN -e "CPAN::Shell->notest('install', 'Monitoring::Plugin')"

install via shinken.io

.. code::

	shinken install rabbitmq

usage
=====

this pack provide 4 hosts templates.

- **rabbitmq**: provide all check of basic health of a rabbitmq server.
- **rabbitmq-exchange**: template to check a specific exchange.
- **rabbitmq-queue**: template to check a specific queue.
- **rabbitmq-showel**. template to check if all showel of a server is running. (require showel plugin)

configuration
=============

see pack/rabbitmq/templates.cfg to see definition in each hosts to see how to customize your commands.


Status
======

Currently we have the following checks:

    check_rabbitmq_aliveness
        Use the /api/aliveness-test API to send/receive a message.

    check_rabbitmq_connections
        Use the /api/connections API to gather details of connections used, their state and their throughput

    check_rabbitmq_exchange
        Use the /api/exchanges API to collect average rates of confirmed, published in and published out messages/second in a period of time on a given exchange.

    check_rabbitmq_objects
        Use a variety of APIs to count instances of various objects on the server. These include vhosts, exchanges, bindings, queues and channels.

    check_rabbitmq_overview
        Use the /api/overview API to collect the number of pending, ready and unacknowledged messages on the server

    check_rabbitmq_partition
        Use the /api/nodes API to check for partitions in a RabbitMQ cluster.

    check_rabbitmq_cluster
        Use the /api/nodes API to check how many node are alive in the cluster.

    check_rabbitmq_queue
        Use the /api/queue API to collect the number of pending, ready and unacknowledged messages and the number of consumers on a given queue or all the queues available. Exclude parameter also works if all queues are checked

    check_rabbitmq_server
        Use the /api/nodes API to gather resource usage of the rabbitmq server node

    check_rabbitmq_shovels
        Use the /api/nodes API check that all the shovels of the given RabbitMQ host are running

    check_rabbitmq_watermark
        Use the /api/nodes API to check to see if mem_alarm has been set to true




credit
======


this pack is a porting of the nagios plugin nagios-plugins-rabbitmq
https://github.com/nagios-plugins-rabbitmq/nagios-plugins-rabbitmq