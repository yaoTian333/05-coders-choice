Publish/Subscribe model is well used in the current service design. It decouples the service providers and consumers so that both sides would not require any knowldege of each other.

This application implements a Publish/Subscribe messaging system with Genserver/Supervisor modules of Elixir. The message consumers subscribe to the events from a topic and the consumers will be notified whenever an event of that topic arrives.

# Preparation

```
# mix deps.get
```

# Interaction

Please replace '192.168.1.12' and '192.168.1.13' with the exact IP addresses.

## Node 1

```
$ iex --name node1@192.168.1.12 --cookie pubsub -S mix
iex(node1@192.168.1.12)> {:ok, provider} = Publisher.start
iex(node1@192.168.1.12)> :global.register_name('provider', provider)
```

## Node 2

```
$ iex --name node2@192.168.1.13 --cookie pubsub -S mix
iex(node2@host)> Node.connect :'node1@192.168.1.12'
iex(node2@host)> provider = :global.whereis_name('provider')
iex(node2@host)> {:ok, subscriber} = Subscriber.start
iex(node2@host)> Publisher.subscribe(provider, 'subs', subscriber)
```

## How to publish a message

```
iex> Publisher.notify(provider, "Hello World!")
```
