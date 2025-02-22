---
Title: Options for Redis Enterprise databases
description: A primer for the configuration options for Redis Enterprise database custom resource definitions.
weight: 35
alwaysopen: false
categories: ["Platforms"]
aliases: [
   /platforms/kubernetes/reference/db-options.md,
   /platforms/kubernetes/reference/db-options/,
   /kubernetes/reference/db-options.md,
   /kubernetes/reference/db-options/,
]
---

The database options are specified in the `spec` section of the database custom resource.
These options include options that you can change and options that are created by the controller for applications or developers. Changes made to the REDB custom resource will override changes made to the database via the admin console or `rladmin` commands.

The most common options are listed below. For a complete list of options, see [Redis Enterprise Database API](https://github.com/RedisLabs/redis-enterprise-k8s-docs/blob/master/redis_enterprise_database_api.md).

### `databasePort`

Manually sets the TCP port on which the database is available. If the port number is not specified, it will be automatically generated.

{{<warning>}}
`databasePort` cannot be added, removed, or changed after database creation.
{{</warning>}}

If the admission controller is installed and configured, it will run validity checks before the REDB creation. If the port is not available, you'll get an error for "port is unavailable." If the port is not valid, you'll get an error for "change databasePort is not allowed."

### `databaseSecretName`

A string containing the name of a secret that contains the desired database password.

If you specify a secret name, you must create an [opaque secret](https://kubernetes.io/docs/concepts/configuration/secret/#opaque-secrets) before you create the
database resource. The operator takes the password from the `password` key in the secret.

To disable authentication for the database,  use an empty string as a value for the `password` key.

If you do not specify a secret name, the operator will create a secret for you with the name
constructed from the database name (`metadata.name`) with "`redb-`" as a prefix.

When the database is created, the secret is updated to include the port and service name for the database,
but the password does not change. If you did not create the secret, it is
also updated with the generated database password.


### `evictionPolicy`

An [eviction policy]({{< relref "/rs/databases/configure/eviction-policy.md">}}) (default: `volatile-lru`)

### `memorySize`

The amount of memory to allocate that is at least 100MB. Values are an integer
suffixed with a unit. For example, values like 1GB, 250MB, etc.

### `persistence`

The value for the [database persistence]({{< relref "/rs/databases/configure/database-persistence.md">}}) setting.

The value is a keyword with the values:

| Value | Description |
| ----- | ----------- |
| disabled | Data is not persisted (default) |
| aofEverySecond | Data is synced to disk every second |
| aofAlways | Data is synced to disk with every write. |
| snapshotEvery1Hour | A snapshot of the database is created every hour |
| snapshotEvery6Hour | A snapshot of the database is created every 6 hours. |
| snapshotEvery12Hour | A snapshot of the database is created every 12 hours. |

### `rackAware`

A boolean that indicates whether the database is [rack-zone aware]({{< relref "/rs/concepts/high-availability/rack-zone-awareness.md">}}) (default: the cluster setting)

### `redisEnterpriseCluster`

The name of the cluster to create the database on.

The value has a single `name` property.
For example, to refer to the `rec` cluster:

```YAML
redisEnterpriseCluster:
   name: rec
```

### `replication`

A boolean that indicates whether in-memory [database replication]({{< relref "/rs/concepts/high-availability/replication.md">}}) is enabled (default: `false`).

When enabled, the database has a replica shard for every master.

### `shardCount`

The number of [database shards]({{< relref "/rs/concepts/high-availability/clustering.md">}}) (default: `1`).

### `tlsMode`

Controls SSL [authentication and encryption]({{<relref "/rs/security/tls">}}) for connections to the database.

| Value | Description |
| ----- | ----------- |
| disabled | no incoming connection to the Database uses SSL (default) |
| enabled | all incoming connections to the Database must use SSL. |
| replica_ssl | databases that replicate from this database must use SSL. |
