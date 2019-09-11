# hnsd

[Github Repo](https://github.com/handshake-org/hnsd)

`hnsd` is a lightweight DNS server written in C
that can resolve Handshake names. The network
is configurable and the code must be rebuilt
to run on a different network, ie testnet vs
mainnet.

Additional arguments to `hnsd` can be passed
to the `docker run` command, for example
additional seeds to connect to using the `-s`
flag.
