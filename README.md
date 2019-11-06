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
  - [Asset registration](#asset-registration)
  - [Asset manifest](#asset-manifest)
  - [Handler manifest](#handler-manifest)
- [Annotations](#annotations)
- [Templates](#templates)
- [Installation from source and contributing](#installation-from-source-and-contributing)

### Overview

This plugin provides native OpenVPN instrumentation for metrics collection of `load-stats` metrics. It is capable of being used with both Sensu Core and Sensu Go. 

### Usage examples

### Configuration

#### Sensu Go
##### Asset manifest
```yml

```
##### Check manifest
```yml
```
#### Sensu Core
##### Check definition
```json
```

## Functionality

## Files
 * bin/metrics-openvpn.rb

## Usage

```
{
  "openvpn-metrics": {
    "host": "1.2.3.4",
    "port": "12345",
    "service": "main"
  }
}
```

## Installation

[Installation and Setup](http://sensu-plugins.io/docs/installation_instructions.html)

## Notes
