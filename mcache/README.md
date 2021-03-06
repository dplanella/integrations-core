# Memcache Check

## Overview

The Agent's memcache check lets you track memcache's memory use, hits, misses, evictions, fill percent, and much more.

## Installation

The memcache check is packaged with the Agent, so simply [install the Agent](https://app.datadoghq.com/account/settings#agent) on your memcache servers. If you need the newest version of the check, install the `dd-check-mcache` package.

## Configuration

Create a file `mcache.yaml` in the Agent's `conf.d` directory:

```
init_config:

instances:
  - url: localhost  # url used to connect to the memcached instance
    port: 11212 # optional; default is 11211
#    socket: /path/to/memcache/socket # alternative to url/port; 'dd-agent' user must have read/write permission
    options:
      items: false # set to true to collect items stats
      slabs: false # set to true to collect slabs stats
#    tags:
#    - optional_tag
```

Restart the Agent to begin sending memcache metrics to Datadog.

## Validation

Run the Agent's `info` subcommand and look for `mcache` under the Checks section:

```
  Checks
  ======
    [...]

    mcache
    -------
      - instance #0 [OK]
      - Collected 26 metrics, 0 events & 1 service check

    [...]
```

## Compatibility

The memcache check is compatible with all major platforms.

## Metrics

See [metadata.csv](https://github.com/DataDog/integrations-core/blob/master/mcache/metadata.csv) for a list of metrics provided by this check.

The check only collects `memcache.slabs.*` metrics if you set `options.slabs: true` in `mcache.yaml`. Likewise, it only collects `memcache.items.*` metrics if you set `options.items: true`.

## Service Checks

`memcache.can_connect`:

Returns CRITICAL if the Agent cannot connect to memcache to collect metrics, otherwise OK.

## Further Reading

Read more about monitoring memcache with Datadog in [this blog post](https://www.datadoghq.com/blog/speed-up-web-applications-memcached/), and how you can instrument Memcached performance metrics with DogStatsD [in this blog post](https://www.datadoghq.com/blog/instrument-memcached-performance-metrics-dogstatsd/)

Learn how to monitor ElastiCache performance metrics with Redis or Memcached in [this blog post](https://www.datadoghq.com/blog/monitoring-elasticache-performance-metrics-with-redis-or-memcached/)
