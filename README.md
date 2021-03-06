aerospike-collectd
====================
Aerospike plugin for collectd.

Release Notes
==============

v0.6.1
------
- Added aerospike.conf

v0.6.0
------
- Added XDR stats (Enterprise 3.7.4+)
- Added more metrics from statistics check
- Reverted certain types in aerospike\_types.db 

v0.5.0
------
- Not compatible with 0.0.0
- Effort will be taken in future releases to preserve compatibility.
- Service level stats now have a context string "service"
- Removed types from aerospike\_types.db that conflicted with collectd's
  default types.
- Added meta stats about this plugins performance.
- Added optional HostNameOverride configuration parameter.

v0.0.0
------
- This package is in early development; backwards compatibility is not
presently considered.

Install
=======

```
sudo pip install -r requirements.txt
```

Highlights from collectd.conf:

```
TypesDB "/opt/collectd-plugins/aerospike_types.db"

<LoadPlugin python>
    Globals true
</LoadPlugin>

<Plugin python>
    ModulePath "/opt/collectd-plugins/"
    LogTraces true
    Interactive false
    Import "aerospike_plugin"
    <Module aerospike_plugin>
        Host   "127.0.0.1"
        Port   3000
        # Prefix "cluster_name"
        # HostNameOverride "clusters.cluster_name.host_name"
    </Module>
</Plugin>
```

Features
========
- Service Level Stats (`asinfo -v "statistics"`)
- Namespace Stats (`asinfo -v "namespace/NAMESPACE_NAME"`)
- Latency Stats (`asinfo -v "latency:"`)
- XDR Stats (`asinfo  -v "dc/DATACENTER_NAME"`)
- Can use Aerospike Security accounts
- (TODO) Configuration Stats (`asinfo -v "get-config:context=CONTEXT"`)
