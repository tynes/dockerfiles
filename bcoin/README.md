# bcoin

[Github Repo](https://github.com/bcoin-org/bcoin)

bcoin looks for config and saves its database
in a `.bcoin` directory. The default location
for this directory is `/opt/.bcoin` in this container.
Be sure to mount that directory into the local
filesystem if you would like to persist data or
easily configure the app.

bcoin is configured with [bcfg](https://github.com/bcoin-org/bcfg)
which can be configured with environment variables and
command line arguments, so it is possible to configure
bcoin at runtime like so

