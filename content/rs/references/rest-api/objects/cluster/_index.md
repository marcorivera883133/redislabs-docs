---
Title: Cluster object
linkTitle: cluster
description: An object that represents a cluster
weight: $weight
alwaysopen: false
categories: ["RS"]
---

An API object that represents the cluster.

| Name | Type/Value | Description |
|------|------------|-------------|
| alert_settings | [alert_settings]({{<relref "/rs/references/rest-api/objects/cluster/alert_settings">}}) object | Cluster and node alert settings |
| cluster_ssh_public_key | string | Cluster's autogenerated SSH public key |
| cm_port | integer, (range:&nbsp;1024-65535) | UI HTTPS listening port |
| cm_session_timeout_minutes | integer (default:&nbsp;15) | The timeout (in minutes) for the session to the CM |
| cnm_http_port | integer, (range:&nbsp;1024-65535) | API HTTP listening port |
| cnm_https_port | integer, (range:&nbsp;1024-65535) | API HTTPS listening port |
| control_cipher_suites | string | Specifies the enabled ciphers for the control plane. The ciphers are specified in the format understood by the BoringSSL library. |
| crdt_rest_client_retries | integer | Maximum number of retries for the REST client used by the Active-Active management API |
| crdt_rest_client_timeout | integer | Timeout for REST client used by the Active-Active management API |
| created_time | string | Cluster creation date (read-only) |
| data_cipher_list | string | Specifies the enabled ciphers for the data plane. The ciphers are specified in the format understood by the OpenSSL library. |
| debuginfo_path | string | Path to a local directory used when generating support packages |
| default_non_sharded_proxy_policy | string (default:&nbsp;single) | Default proxy_policy for newly created non-sharded databases' endpoints (read-only) |
| default_sharded_proxy_policy | string (default:&nbsp;all-master-shards) | Default proxy_policy for newly created sharded databases' endpoints (read-only) |
| email_alerts | boolean (default:&nbsp;false) | Send node/cluster email alerts (requires valid SMTP and email_from settings) |
| email_from | string | Sender email for automated emails |
| envoy_max_downstream_connections | integer, (range:&nbsp;100-2048) | The max downstream connections envoy is allowed to open |
| handle_redirects | boolean (default:&nbsp;false) | Handle API HTTPS requests and redirect to the master node internally |
| http_support | boolean (default:&nbsp;false) | Enable/disable HTTP support |
| min_control_TLS_version | '1' <br />'1.1' <br />'1.2' <br />'1.3' | The minimum version of TLS protocol which is supported at the control path |
| min_data_TLS_version | '1' <br />'1.1' <br />'1.2' | The minimum version of TLS protocol which is supported at the data path |
| min_sentinel_TLS_version | '1' <br />'1.1' <br />'1.2' | The minimum version of TLS protocol which is supported at the data path |
| name | string | Cluster's fully qualified domain name (read-only) |
| password_complexity | boolean (default:&nbsp;false) | Enforce password complexity policy |
| password_expiration_duration | integer (default:&nbsp;0) | The number of days a password is valid until the user is required to replace it |
| proxy_certificate | string | Cluster's proxy certificate |
| proxy_max_ccs_disconnection_time | integer | Cluster-wide proxy timeout policy between proxy and CCS |
| rack_aware | boolean | Cluster operates in a rack-aware mode (read-only) |
| s3_url | string | Specifies the URL for S3 export and import |
| saslauthd_ldap_conf | string | saslauthd LDAP configuration |
| sentinel_cipher_suites | array | Specifies the list of enabled ciphers for the sentinel service. The supported ciphers are ones that were implemented by the [cipher_suits.go](<https://golang.org/src/crypto/tls/cipher_suites.go>) package. |
| sentinel_ssl_policy | 'allowed'<br />'disabled' <br />'required' | Is ssl for the Discovery Service required/disabled/allowed |
| slave_ha | boolean (default:&nbsp;false) | Enable the replica high-availability mechanism (read-only) |
| slave_ha_bdb_cooldown_period | integer (default:&nbsp;86400) | Time in seconds between runs of the replica high-availability mechanism on different nodes on the same database (read-only) |
| slave_ha_cooldown_period | integer (default:&nbsp;3600) | Time in seconds between runs of the replica high-availability mechanism on different nodes (read-only) |
| slave_ha_grace_period | integer (default:&nbsp;900) | Time in seconds between a node failure and when the replica high-availability mechanism starts relocating shards (read-only) |
| slowlog_in_sanitized_support | boolean | Whether to include slowlogs in the sanitized support package |
| smtp_host | string | SMTP server for automated emails |
| smtp_password | string | SMTP server password |
| smtp_port | integer | SMTP server port for automated emails |
| smtp_tls_mode | 'none'<br />'starttls'<br />'tls' | Specifies which TLS mode to use for SMTP access |
| smtp_use_tls | boolean (default:&nbsp;false) | Use TLS for SMTP access (deprecated, use smtp_tls_mode field instead) |
| smtp_username | string | SMTP server username (pattern does not allow special characters &,\<,>,") |
| syncer_certificate | string | Cluster's syncer certificate |
| upgrade_mode | boolean (default:&nbsp;false) | Is cluster currently in upgrade mode |
| use_ipv6 | boolean (default:&nbsp;true) | Should redislabs services listen on ipv6 |
| wait_command | boolean (default:&nbsp;true) | Supports Redis wait command (read-only) |
