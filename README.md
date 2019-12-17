[![Bonsai Asset Badge](https://img.shields.io/badge/Sensu%20OpenVPN%20Plugin-Download%20Me-brightgreen.svg?colorB=89C967&logo=sensu)](https://bonsai.sensu.io/assets/sensu-plugins/sensu-plugins-openvpn)
[ ![Build Status](https://travis-ci.org/sensu-plugins/sensu-plugins-openvpn.svg?branch=master)](https://travis-ci.org/sensu-plugins/sensu-plugins-openvpn)
[![Gem Version](https://badge.fury.io/rb/sensu-plugins-openvpn.svg)](http://badge.fury.io/rb/sensu-plugins-openvpn)
[![Code Climate](https://codeclimate.com/github/sensu-plugins/sensu-plugins-openvpn/badges/gpa.svg)](https://codeclimate.com/github/sensu-plugins/sensu-plugins-openvpn)
[![Test Coverage](https://codeclimate.com/github/sensu-plugins/sensu-plugins-openvpn/badges/coverage.svg)](https://codeclimate.com/github/sensu-plugins/sensu-plugins-openvpn)
[![Dependency Status](https://gemnasium.com/sensu-plugins/sensu-plugins-openvpn.svg)](https://gemnasium.com/sensu-plugins/sensu-plugins-openvpn)

## Sensu OpenVPN Metrics Plugin

- [Overview](#overview)
- [Usage examples](#usage-examples)
- [Configuration](#configuration)
  - [Sensu Go](#sensu-go)
    - [Asset registration](#asset-registration)
    - [Asset definition](#asset-definition)
    - [Check definition](#check-definition)
  - [Sensu Core](#sensu-core)
    - [Check definition](#check-definition)
  - [Additional information](#additional-information)
- [Files](#files)
- [Installation](#installation)


### Overview

This plugin provides native OpenVPN instrumentation for metrics collection of `load-stats` metrics. It is capable of being used with both Sensu Core and Sensu Go. 

The Sensu assets packaged from this repository are built against the Sensu ruby runtime environment. When using these assets as part of a Sensu Go resource (check, mutator or handler), make sure you include the corresponding Sensu ruby runtime asset in the list of assets needed by the resource.  The current ruby-runtime assets can be found [here](https://bonsai.sensu.io/assets/sensu/sensu-ruby-runtime) in the [Bonsai Asset Index](bonsai.sensu.io)

### Usage examples
```
Usage: metrics-openvpn.rb (options)
    -h, --host HOST                  Host to connect to
    -p, --port PORT                  Port to connect to
    -r, --prompt PROMPT              Initial prompt for OpenVPN admin interface
    -s, --scheme SCHEME              Metric naming scheme, text to prepend to metric
    -e, --service SERVICE            If more than one openvpn service is running here, name this one to identify it
    -t, --timeout TIMEOUT            Connection timeout
```
### Configuration

#### Sensu Go
##### Asset registration

Assets are the best way to make use of this handler. If you're not using an asset, please consider doing so! If you're using sensuctl 5.13 or later, you can use the following command to add the asset: 

`sensuctl asset add sensu/sensu-email-handler`

If you're using an earlier version of sensuctl, you can download the asset definition from [this project's Bonsai Asset Index page](https://bonsai.sensu.io/assets/sensu-plugins/sensu-plugins-openvpn).

##### Asset definition
```yml
---
type: Asset
api_version: core/v2
metadata:
  name: sensu-plugins-openvpn_centos_amd64
  labels: 
  annotations:
    io.sensu.bonsai.url: https://bonsai.sensu.io/assets/asachs01/sensu-plugins-openvpn
    io.sensu.bonsai.api_url: https://bonsai.sensu.io/api/v1/assets/asachs01/sensu-plugins-openvpn
    io.sensu.bonsai.tier: Community
    io.sensu.bonsai.version: 1.0.4-pre
    io.sensu.bonsai.namespace: asachs01
    io.sensu.bonsai.name: sensu-plugins-openvpn
    io.sensu.bonsai.tags: experimental, pre-release
spec:
  url: https://assets.bonsai.sensu.io/1ae7ab5fd0421f1c216d92bd26c3abe7c50d3577/sensu-plugins-openvpn_1.0.4-pre_centos_linux_amd64.tar.gz
  sha512: bc2ab56354ec9fe5ca468c391000bcdc1d8893818561c21cc6bea6e3fde5c405434bf01e867c4de383c5626601c9ee19c8a5c0af87d0b2debc663c93c172f677
  filters:
  - entity.system.os == 'linux'
  - entity.system.arch == 'amd64'
  - entity.system.platform_family == 'rhel'
```
##### Check definition
```yml
---
type: CheckConfig
api_version: core/v2
metadata:
  name: metrics-openvpn
  namespace: default
spec:
  command: 'metrics-openvpn.rb'
  runtime_assets:
  - sensu-plugins/sensu-plugins-openvpn
  - sensu/sensu-ruby-runtime
  subscriptions:
  - linux
  interval: 10
  timeout: 5
  output_metric_format: graphite_plaintext
  output_metric_handlers:
  - influxdb
```
#### Sensu Core
##### Check definition
```json
{
  "checks": {
    "metrics-openvpn": {
      "command": "metrics-openvpn.rb",
      "subscribers": ["openvpn"],
      "interval": 10,
      "refresh": 10,
      "handlers": ["influxdb"]
    }
  }
}
```
#### Additional information
This plugin can be configured in several ways. The following denotes the order of precedence for how values for this plugin are defined

1. Values defined locally in `/etc/sensu/conf.d/*.json`

2. Command line options passed via --host and --port

3. Built-in defaults (displayed with --help)

##### Example configuration file
This plugin can be used with a configuration file living on disk as noted above. See the example below:
```json
{
  "openvpn-metrics": {
    "host": "1.2.3.4",
    "port": "12345",
    "service": "main"
  }
}
```

## Files
 * bin/metrics-openvpn.rb

## Installation

### Sensu Go

See the instructions above for [asset registration](#asset-registration)

### Sensu Core
Install and setup plugins on [Sensu Core](https://docs.sensu.io/sensu-core/latest/installation/installing-plugins/)
