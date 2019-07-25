[<< Back to Table of Contents](README.md)

# Rabbit MQ

## Admin Console

- http://localhost:15672/
- guest / guest 
-

## Message Types

- STOMP ( SEND semantic ) HTTP-like design. SENDs to a "destination" ( Simple Text Oriented Message Protocol )

- MQTT ( Machine to Machine ) Push-subscribe messaging - dial up / satellite / low bandwith / high latency / mobile / IT

- AMPQ ( Advanced Message Queuing Protocol ) Reliable / Interoperable . Highly standardized. JP Morgan uses it to process billions of messages a day. 

## AMQP Benefits

- Ability to use different client



## Setup Management Console

- Open CMD Prompt with Admin privileges
- C:\...\rabbitmq-server-3.5.6\sbin>  
- SET HOMEDRIVE=C:
- rabbitmq-service remove
- rabbitmq-service install
- rabbitmq-plugins.bat enable rabbitmq_management
- rabbitmq-service stop
- rabbitmq-service start


[<< Back to Table of Contents](README.md)
