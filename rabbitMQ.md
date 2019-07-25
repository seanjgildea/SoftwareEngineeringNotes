[<< Back to Table of Contents](README.md)

# Rabbit MQ

## Admin Console

- http://localhost:15672/
- guest / guest 
-

## Message Types

- STOMP ( SEND semantic ) HTTP-like design. SENDs to a "destination" ( Simple Text Oriented Message Protocol )

- MQTT ( Machine to Machine ) Push-subscribe messaging - dial up / satellite / low bandwith / high latency / mobile / IT

- AMPQ 



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
