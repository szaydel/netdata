<!--startmeta
custom_edit_url: "https://github.com/netdata/netdata/edit/master/collectors/freebsd.plugin/integrations/net.isr.md"
meta_yaml: "https://github.com/netdata/netdata/edit/master/collectors/freebsd.plugin/metadata.yaml"
sidebar_label: "net.isr"
learn_status: "Published"
learn_rel_path: "Data Collection/FreeBSD"
message: "DO NOT EDIT THIS FILE DIRECTLY, IT IS GENERATED BY THE COLLECTOR'S metadata.yaml FILE"
endmeta-->

# net.isr

Plugin: freebsd.plugin
Module: net.isr

<img src="https://img.shields.io/badge/maintained%20by-Netdata-%2300ab44" />

## Overview

Collect information about system softnet stat.

The plugin calls `sysctl` function to collect necessary data.

This collector is supported on all platforms.

This collector supports collecting metrics from multiple instances of this integration, including remote instances.


### Default Behavior

#### Auto-Detection

This integration doesn't support auto-detection.

#### Limits

The default configuration for this integration does not impose any limits on data collection.

#### Performance Impact

The default configuration for this integration is not expected to impose a significant performance impact on the system.


## Metrics

Metrics grouped by *scope*.

The scope defines the instance that the metric belongs to. An instance is uniquely identified by a set of labels.



### Per net.isr instance

These metrics show statistics about softnet stats.

This scope has no labels.

Metrics:

| Metric | Dimensions | Unit |
|:------|:----------|:----|
| system.softnet_stat | dispatched, hybrid_dispatched, qdrops, queued | events/s |

### Per core



This scope has no labels.

Metrics:

| Metric | Dimensions | Unit |
|:------|:----------|:----|
| cpu.softnet_stat | dispatched, hybrid_dispatched, qdrops, queued | events/s |



## Alerts


The following alerts are available:

| Alert name  | On metric | Description |
|:------------|:----------|:------------|
| [ 1min_netdev_backlog_exceeded ](https://github.com/netdata/netdata/blob/master/health/health.d/softnet.conf) | system.softnet_stat | average number of dropped packets in the last minute due to exceeded net.core.netdev_max_backlog |
| [ 1min_netdev_budget_ran_outs ](https://github.com/netdata/netdata/blob/master/health/health.d/softnet.conf) | system.softnet_stat | average number of times ksoftirq ran out of sysctl net.core.netdev_budget or net.core.netdev_budget_usecs with work remaining over the last minute (this can be a cause for dropped packets) |
| [ 10min_netisr_backlog_exceeded ](https://github.com/netdata/netdata/blob/master/health/health.d/softnet.conf) | system.softnet_stat | average number of drops in the last minute due to exceeded sysctl net.route.netisr_maxqlen (this can be a cause for dropped packets) |


## Setup

### Prerequisites

No action required.

### Configuration

#### File

The configuration file name for this integration is `netdata.conf`.
Configuration for this specific integration is located in the `[plugin:freebsd:net.isr]` section within that file.

The file format is a modified INI syntax. The general structure is:

```toml
[section1]
    option 1 = some value
    option 2 = some other value

[section2]
    option 3 = some third value
```
You can edit the configuration file using the `edit-config` script from the
Netdata [config directory](https://github.com/netdata/netdata/blob/master/docs/configure/nodes.md#the-netdata-config-directory).

```bash
cd /etc/netdata 2>/dev/null || cd /opt/netdata/etc/netdata
sudo ./edit-config netdata.conf
```
#### Options



<details><summary>Config options</summary>

| Name | Description | Default | Required |
|:----|:-----------|:-------|:--------:|
| netisr | Enable or disable general vision about softnet stat metrics. |  | False |
| netisr per core | Enable or disable softnet stat metric per core. |  | False |

</details>

#### Examples
There are no configuration examples.

