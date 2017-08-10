# Kubelet Integration

## Overview

This integration gets Kubernetes metrics from kubelet

* Visualize and monitor kubelet stats
* Be notified about kubelet failovers and events.

## Installation

Install the `dd-check-kubelet` package manually or with your favorite configuration manager

## Configuration

Edit the `kubelet.yaml` file to point to your server and port, set tags to send along with metrics.

## Validation

When you run `datadog-agent info` you should see something like the following:

    Checks
    ======

        kubelet
        -----------
          - instance #0 [OK]
          - Collected 39 metrics, 0 events & 7 service checks

## Compatibility

The kubelet check is compatible with all major platforms where Kubernetes runs.
