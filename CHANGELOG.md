# Change Log
This project adheres to [Semantic Versioning](http://semver.org/).

This CHANGELOG follows the format listed at [Keep A Changelog](http://keepachangelog.com/)

## [Unreleased]

## [2.0.0] 2019-12-16
### Security
- Updated yard development dependency from '~> 0.8.0' to '~> 0.9.20'

### Changed
- Updated rubocop development dependency from '~> 0.40.0' to '~> 0.50.0' 

### Added
- Travis build automation to generate Sensu Asset tarballs that can be used n conjunction with Sensu provided ruby runtime assets and the Bonsai Asset Index
- Require latest sensu-plugin for Sensu Go support

### Breaking change
- Updates minimum required ruby version to 2.3. Drop unsupported ruby versions.
- Update dependancy on sensu-plugin to 4.0

## [1.0.0] 2017-07-14
### Added
- Testing on Ruby 2.3.0 & 2.4.1

### Breaking Changes
- Removed support for Ruby 1.9.3

## [0.0.3] - 2016-08-10
### Changed
- Updated sensu-plugin dependency from `= 1.2.0` to `~> 1.2`

## [0.0.2] - 2015-07-14
### Changed
- updated sensu-plugin gem to 1.2.0

## 0.0.1 - 2015-07-04
### Added
- initial release

[Unreleased]: https://github.com/sensu-plugins/sensu-plugins-openvpn/compare/2.0.0...HEAD
[2.0.0]: https://github.com/sensu-plugins/sensu-plugins-openvpn/compare/1.0.0...2.0.0
[1.0.0]: https://github.com/sensu-plugins/sensu-plugins-openvpn/compare/0.0.3...1.0.0
[0.0.3]: https://github.com/sensu-plugins/sensu-plugins-openvpn/compare/0.0.2...0.0.3
[0.0.2]: https://github.com/sensu-plugins/sensu-plugins-openvpn/compare/0.0.1...0.0.2
