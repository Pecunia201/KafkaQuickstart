# Kafka Quickstart

This is my implementation of the official [Kafka Quick Start](https://developer.confluent.io/get-started/c).

## Packages Required

- `librdkafka`
- `pkg-config`
- `glib-2.0`

> I had to manually set the include directories in `CMakeLists.txt` for librdkafka, and you might need to specify different paths depending on your environment. This setup was done using WSL.

## Installation

1. **Install** [Docker Desktop](https://docs.docker.com/desktop/) **or** [Docker Engine](https://docs.docker.com/engine/install/)

2. **Install** [Confluent CLI](https://docs.confluent.io/confluent-cli/current/install.html)

## Start Kafka Broker

To start the Kafka broker, use the following command:

```
confluent local kafka start
```

## Run the Consumer and Producer
```
./consumer
```
```
./producer
```
