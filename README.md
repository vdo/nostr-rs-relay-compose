# nostr-rs-relay-compose

Docker compose deployment for [nostr](https://github.com/fiatjaf/nostr), using the Rust relay [nostr-rs-relay](https://sr.ht/~gheartsfield/nostr-rs-relay/) and [Traefik](https://traefik.io/).

## Requirements

- Docker (tested with 20.10.12)

- Docker compose (tested with 1.29.2)

## Instructions

1. Edit the .env var and adjust it to your needs (domain, email for Let's Encrypt, ...)

2. Edit the config file `config.toml` with your preferred settings.

3. Pull and start:

```
docker-compose pull
docker-compose up -d
```

4. Check the logs:

```
docker-compose logs nostr-rs-relay

```

5. Done! You can test the WebSocket connectivity with [websocat](https://github.com/vi/websocat):

```
> echo '["REQ", "test", {}]' | websocat -1 -n wss://nostr.unknown.place
["EVENT","test",{"id":"19070d74d81118aa9b412b597615f380778ededd1df71f551a5aa83dd02ae91b","pubkey":"48bd69736fa9e0a322aa132ec7613313b84fd064319c4f0ef4fdb8a55a66ad09","created_at":1645103669,"kind":1,"tags":[],"content":"this is a test","sig":"517f8073f2ea8d5e2de6d51b42e3c32d79994b02d744a1d28e5bd56213af0248e64119ec5d034dc5b3fbc4d6d535238b5cb3683752d3a392be5715136a063362"}]
```
