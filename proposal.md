Name: YAO TIAN          ID: 4752 0724

## Proposed Project

Publish/Subscribe model is well used in the current service design. It decouples the service providers and consumers so that both sides would not require any knowldege of each other.


## Outline Structure

This application implements a Publish/Subscribe messaging system with Genserver/Supervisor modules of Elixir. The message consumers subscribe to the events from a topic and the consumers will be notified whenever an event of that topic arrives.

