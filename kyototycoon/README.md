# Kyototycoon Integration

## Overview

The Agent's Kyototycoon check tracks get, set, and delete operations, and lets you monitor replication lag.

## Installation

The Kyototycoon check is packaged with the Agent, so simply [install the Agent](https://app.datadoghq.com/account/settings#agent) on your Kyototycoon servers. If you need the newest version of the check, install the `dd-check-kyototycoon` package.

## Configuration

Create a file `kyototycoon.yaml` in the Agent's `conf.d` directory:

```
init_config:

instances:
#  Each instance needs a report URL. 
#  name, and optionally tags keys. The report URL should
#  be a URL to the Kyoto Tycoon "report" RPC endpoint.
#
#  Complete example:
#
- report_url: http://localhost:1978/rpc/report
#   name: my_kyoto_instance
#   tags:
#     foo: bar
#     baz: bat
```

## Validation

Run the Agent's `info` subcommand and look for `kyototycoon` under the Checks section:

```
  Checks
  ======
    [...]

    kyototycoon
    -------
      - instance #0 [OK]
      - Collected 26 metrics, 0 events & 1 service check

    [...]
```

## Compatibility

The kyototycoon check is compatible with all major platforms.

## Metrics

See [metadata.csv](https://github.com/DataDog/integrations-core/blob/master/kyototycoon/metadata.csv) for a list of metrics provided by this check.

## Service Checks

`kyototycoon.can_connect`:

Returns CRITICAL if the Agent cannot connect to Kyototycoon to collect metrics, otherwise OK.
