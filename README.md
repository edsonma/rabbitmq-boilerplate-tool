# RabbitMQ Boilerplate Tool
RabbitMQ boilerplate setup for fun and exploration.

# RabbitMQ Overview

**RabbitMQ** is an open-source message broker that facilitates communication between applications by implementing message queues. It allows producers (applications that send messages) to send messages to consumers (applications that process messages) through queues, ensuring reliable message delivery, load balancing, and fault tolerance.

## Key Concepts

- **Producer**: Sends messages to RabbitMQ.
- **Consumer**: Receives and processes messages from RabbitMQ.
- **Queue**: Buffers messages until consumed.
- **Exchange**: Routes messages to queues based on rules.
- **AMQP**: Default protocol for message communication in RabbitMQ.

## Use Cases

- **Decoupling services** for asynchronous communication.
- **Task queues** to distribute workloads.
- **Event-driven architectures** for triggering actions across systems.
- **Reliable message delivery** through persistence and acknowledgments.

## Features

- **Message persistence**, **routing**, and **monitoring** tools.
- Supports multiple protocols (e.g., AMQP, MQTT).
- Extensible with plugins and supports **clustering** for high availability.

RabbitMQ is widely used for scalable, reliable messaging in distributed systems and microservices architectures.

## Getting Started

To launch the RabbitMQ environment using Docker:

```bash
docker-compose up
```

## Credentials

To automatically add users without needing to manually configure them through the web/UI management plugin, refer to this helpful [StackOverflow discussion](https://stackoverflow.com).

### Default Username/Password

- **Username**: `mqadmin`
- **Password**: `mq4dm1n_pass`

## Enabled Plugins

The `enabled_plugins` file in RabbitMQ defines which plugins are active on a RabbitMQ node. This file is crucial as it allows you to extend RabbitMQ's core functionality with additional features like management interfaces, protocol support, monitoring tools, or custom exchange types.

### Location of `enabled_plugins` File

- **Linux/Unix**: `/etc/rabbitmq/enabled_plugins` or `/var/lib/rabbitmq/enabled_plugins`
- **Windows**: `%AppData%\RabbitMQ\enabled_plugins`

### Plugins Enabled, in this project, by Default

- **rabbitmq_management**
  Provides a web-based user interface (UI) and HTTP API for managing RabbitMQ. This allows you to monitor and manage RabbitMQ clusters.

- **rabbitmq_mqtt**
  Enables RabbitMQ to function as an MQTT broker, supporting the lightweight MQTT protocol, often used in IoT applications.

- **rabbitmq_delayed_message_exchange**
  Allows for delayed message delivery, where messages can be delayed for a specific amount of time before being routed to the appropriate queue.

- **rabbitmq_prometheus**
  Integrates RabbitMQ with Prometheus, enabling it to expose internal metrics (like message rates, queue sizes, etc.) for monitoring.

## Listening Ports

RabbitMQ uses several ports to handle different protocols and functionalities:

- **5672**
  - **Protocol**: AMQP (Advanced Message Queuing Protocol)
  - Default port for RabbitMQ messaging operations.

- **15672**
  - **Protocol**: HTTP
  - Used for RabbitMQ's Management Plugin (web-based management UI and API).

- **15692**
  - **Protocol**: HTTP
  - Port used for Prometheus metrics, allowing monitoring services to collect RabbitMQ metrics.

- **1883**
  - **Protocol**: MQTT (Message Queuing Telemetry Transport)
  - The port for handling MQTT connections, typically used in IoT environments.

### perfTest Tool  
The perfTest tool in the docker-compose.yml service is designed to simulate a messaging workload on RabbitMQ.

      ./runjava.sh com.rabbitmq.perf.PerfTest
      --uri amqp://mqadmin:mq4dm1n_pass@rabbitmq:5672 --producers 1 --consumers 1
      --rate 100 --time 60 --size 1024

* --uri amqp://mqadmin:mq4dm1n_pass@rabbitmq:5672: Connects to the RabbitMQ instance at rabbitmq:5672 using the credentials mqadmin and mq4dm1n_pass.
* --producers 1: Uses 1 message producer.
* --consumers 1: Uses 1 message consumer.
* --rate 100: Sends 100 messages per second.
* --time 60: Runs the test for 60 seconds.
* --size 1024: Each message is 1024 bytes in size.

This test measures the performance of RabbitMQ under a load of 100 messages per second with 1 producer and 1 consumer.

#### Future Improvement
To make the test more flexible, the hardcoded test command in the docker-compose can be extracted into customizable scenarios for different performance test cases.


## 🚀 Contribute and Improve the Project

We’re always looking for ways to enhance this RabbitMQ boilerplate! Here’s how you can contribute:

- **Submit Pull Requests**: If you have improvements or new features, feel free to submit a PR.
- **Report Issues**: Found a bug or have suggestions? Open an issue, and let’s make this project better together.
- **Share Your Ideas**: Have thoughts on how to extend the boilerplate? Leave a comment or start a discussion!

-- 
**Thank you for any contributions! Every effort helps create a greater understanding of RabbitMQ and its capabilities. Happy Coding! 📚📚📚**