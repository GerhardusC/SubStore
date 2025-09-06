# Sub Store

## About

This is a very simple lightweight MQTT data collection layer. The program will save all messages to a chosen base topic into a SQLite database. If the message can be parsed into a number, it is saved in the 'measurements' table, otherwise it is saved in the 'logs' table.

In addition to the db storage, this program also stores instantaneous values for each topic in a Redis instance. Quite simply, the topic is used as the key for each instantaneous value in Redis.

## Installation

Currently, if you are running an x86 machine on linux, you may choose to install this program using the dedicated [MQTTui](https://github.com/GerhardusC/MQTTui) project, otherwise you must build from source.

Ensure you have the rust toolchain installed and run:
`cargo build --release`

You will find the executable output as `./target/release/substore`

## Usage
It is recommended to set this program up as a startup service to ensure it is always running. The easiest way to do this is again through the [MQTTui](https://github.com/GerhardusC/MQTTui) configuration utility.

Launch options:
  -d, --db-path <DB_PATH>        Path to database [default: ./dev.db]
  -t, --base-topic <BASE_TOPIC>  Base topic to subscribe to, if omitted, you will be subscribed to /# [default: ]
  -b, --broker-ip <BROKER_IP>    IP or domain name of mqtt broker [default: localhost]
  -h, --help                     Print help
  -V, --version                  Print version

