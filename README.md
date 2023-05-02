# Mote
Mote is a protocol that is designed to replace MQTT. It works like an API server for frontend clients while also being an MQTT server for embedded devices; taking the best of both worlds.  On MQTT, clients do not obtain information from the server or from other clients by making requests, instead they make subscriptions and data is always kept in sync, similar to GraphQL subscriptions, but without all the boilerplate.

# Mote-broker
Relpaces the broker in a typical MQTT system.
https://github.com/cyates559/mote-broker

# Mote-webapp
(Coming soon)
A ReactJS client for controlling and managing a Mote system

# Mote-micro
(Coming soon)
A Mote arduino client/smart device library

# Mote-node
(Coming soon)
A Mote python client/smart device library

 # Key differences between Mote and MQTT:
* MQTT can recieve one message per packet, while Mote can handle an entire tree of messages per a single packet.
* MQTT responds to subscriptions one message/packet at a time, while Mote can respond with a tree of messages. 
* When a client creates a subscription to a topic with wildcards and retained values, it recieves all the relevant messages back in one action, this allows the client to know when it has recieved all the relevant messages.
  * This allows Mote to replace typical request/response flows with a flow that we call subscribe/response/update;  Clients can make a request, recieve a response, and then any time the data from that response changes they'll also receive real time updates. 
  * This flow means a client can never have stale data without being disconnected from the server.

 # Future plans:
* Polish and release the libraries that haven't been open sourced yet.
* Possibly a type system instead of using strings/bytes for every field.
  * We'd love to figure out a way to do this that doesn't break the remaining compatibility we have with MQTT
* A system for keeping track of what commands are available.
  * A name, list of parameters and types, and possibly a description for each command that gets registered.
