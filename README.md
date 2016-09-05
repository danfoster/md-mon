MD Storage Array Monitor
========================

This following script extracts performance statistics from Dell MD Storage Arrays and outputs them in a format suitable to be consumed by [`collectd`](https://collectd.org/).

While this has only been tested on Dell MD arrays, it should work on any LSI based storage controller.

Usage
-----

This script should be called by the `collectd` [`exec`](https://collectd.org/documentation/manpages/collectd-exec.5.shtml) plugin. It takes 3 arguments

 * *name* - Friendly name of your arrays
 * *controller_a* - Hostname of controller A
 * *controller_b* - Hostname of controller B

For example:

```
LoadPlugin  exec
<Plugin exec>
  Exec "operator" "/opt/md-mon/md-mon" "storage.example.com" "storage_a.example.com" "storage_b.example.com"
</Plugin>
```

Metrics
-------

The plugin instance will be the name of the Virtual Disk.

The type instance will be one of the following:
 
 * `latency`
 * `throughput`
 * `primary_write_cache_hit`
 * `iops`
 * `primary_read_cache_hit`
 * `read_ratio`
