# Mote
Mote is a protocol that is designed to replace MQTT. Mote is an event-based data store that maintains support for MQTT devices. With Mote, all clients are connected to the data in real-time: data is always kept in sync and cannot go stale.  Subscriptions are similar to GraphQL subscriptions, but without all the boilerplate -- the server needs no code or configuration, it works out of the box.

The Mote protocol embraces simplicity: simple tools, when designed very carefully, can fill many roles and solve many problems.

## Mote-broker
Relpaces the broker in a typical MQTT system.
https://github.com/cyates559/mote-broker

## Mote-native
A React Native client for Mote, includes modules for controlling different devices
https://github.com/cyates559/mote-native

## Mote-node
(this will be open-sourced soon)
A Mote python client/smart device library

## Mote-micro
(this will be open-sourced after mote-node)
A set of C++ libraries for microcontrollers like RP2040 for using various sensors and outputs with Mote

## Key differences between Mote and MQTT:
* MQTT can recieve one message per packet.  If you subscribe to a wildcard topic that can have multiple messages, you'll get those messages back one-at-a-time from the Broker/server.
* Mote can deal with message trees.  Using the `graft` flag, a client can publish many messages to a topic wildcard.  These messages can all be retained and rebroadcast as one action/publish message. -- Basically, publish messages can contain wildcards and can be structured as a tree.
  * If Alice is subscribed to topic A and Bob publishes a tree of messages to a different wildcard topic B, then Alice will recieve only one message for topic A that contains all the changes Bob's message made... this will happen regardless of the differences between topic A and topic B.  When any data relevant to topic A is updated, Alice will always recieve a data structure that can be used to update her previous data structure-- the message that is sent to Alice will always be labeled for topic A.

 ## Future plans:
* Create a new storage style which should:
  * enable subscribing to slices of data and listening as those slices grow. (realtime pagination)
  * enable strict typing
  * partitioning data in different tables
* Polish and release the libraries that haven't been open sourced yet.
