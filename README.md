# vault-graylog-content-pack

[Graylog](http://graylog.org) content pack to parse [Vault](https://vaultproject.io) audit logs.

**NOTE**
I am a aware the Graylog Pipelines are a better fit for this, and I am using Pipelines for my own use of Vault.
I'll add a Pipeline to the content pack (that will also reformat the main message to no longer be a big blob of
JSON) as soon as [Graylog allows to include Pipelines in Content Packs](https://github.com/Graylog2/graylog2-server/issues/2507)

**This content pack contains**

* A TCP listner on port 5553, with extractors to parse the audit log JSON,
  as well as adding fields for the vault mount and the name of the secret accessed/removed.
* 3 basic streams to look at audit logs

## Configuring Vault

Vaults [Socket Audit Backend](https://www.vaultproject.io/docs/audit/socket.html) can be used
to send audit logs to Graylog.

To enable a socket audit backend use:

```
vault audit-enable socket address YOUR_GRAYLOG_HOST:5553
```

Be aware that at this point Vault does not support encrypted connections
in the socket backend so audit logs will be sent in plain text.
