# Change Log

## 6.0.0
- Improved channel pool management (includes a breaking config change - see https://github.com/guidesmiths/rascal#channel-pooling).

## 5.1.0
### Added
- Added potential for flow control / throttling via broker 'busy' and 'ready' events.

## 5.0.0
### Updated
- Wait for subscriber channels to be closed before shutting down the broker
- Reduced default close channel deferral from 1 minute to 10 seconds in default config and from 1 minute to 100ms in test config

## 4.7.0
### Updated
- Dependencies

### Added
- Support for active/passive connection management

## 4.6.2
### Fixed
- Fixed a bug where you could not re-initialise a vhost

## 4.6.1
### Added
- Automated codeclimate reporting

### Fixed
- Fixed a bug where the connection index could be undefined

## 4.6.0
### Updated
- Fixes for #60 and #61. Thanks @rossj.
- Depend on amqplib ^0.5.5

## 4.5.2
### Updated
- Depend on version 0.5.3 of amqplib (peer) until https://github.com/squaremo/amqp.node/issues/534 is fixed

## 4.5.1
### Updated
- Depend on version 0.5.3 of amqplib until https://github.com/squaremo/amqp.node/issues/534 is fixed
- Update dependencies

## 4.5.0
### Updated
- Replaced request with superagent. Thanks @ksnll
- Updated dependencies
- Added node 12 to travis config

## 4.4.0
### Updated
- Throw error when using cluster based redeliveries counter outside of a cluster

## 4.3.1
### Updated
- Dependencies
- Moved amqplib to peer dependency

## Added
- broker.connect(vhost)

## 4.2.1
### Updated
- Dependencies
- Fixed vararg related bug in Broker.create

## 4.2.2
### Updated
- Updated various dev dependencies
- Readme
- Switched from istanbul to nyc
- Fix flakey travis tests

## 4.2.1
### Updated
- Updated lodash

## 4.2.0
### Added
- Support for RabbitMQs default exchange

## 4.1.0
### Added
- Publisher error events are passed the messageId where possible

## 4.0.0
### Updated
- Improved connection failure error message
- It is possible to go async between broker.subscribe and subscription.on('message'). This unlocks the possibility of promise support.
- Support promises
- Discourage use of broker.init

## 3.2.3
### Updated
- Fix connection handler leak caused by re-subscription
- Fix channel leak when channel.consume fails
- amqplib version to 0.5.3
- test on Node 11

## 3.2.2
### Added
- Some additional debug

## 3.2.1
### Fixed
- Catch and return encryption errors via publish callback
### Added
- Assert vhosts into exhistence using the RabbitMQ management API

### Updated
- Changed new Buffer() to Buffer.from to silence Node 10 deprecation warning

## 3.2.0
### Added
- Transparent encryption / decryption

## 3.1.3
### Updated
- Modernise code style

## 3.1.2
### Updated
- Fix redelivery counter defaults

## 3.1.1
### Updated
- Fix channelMax default

## 3.1.0
###  Added
- Handling of redelivery counter errors and timeouts

## 3.0.0
### Updated
- Using lodash defaultsDeep instead of merge-defaults (fixes hoek vulnerability). The behaviour seems consistent but releasing as a breaking change as a precaution.
- Unqualified default publications and subscriptions are no longer supported. See https://github.com/guidesmiths/rascal/issues/20
- Testing on node 10

## 2.12.2
### Updated
- Update dependencies (fixes hoek vulnerability)

## 2.12.1
### Updated
- Fixed bug that prevented publication from emitting channel errors

## 2.12.0
### Updated
- Update dependencies
- Update dev dependencies

## 2.11.3
### Updated
- npm issue

## 2.11.2
### Updated
- npm issue

## 2.11.1
### Fixed
- Fixed undefined error in Vhost.bounce

## 2.11.0
### Fixed
- Support for queue and exchange names containeing period and hyphens

## 2.10.0
### Fixed
- Workaround for non deterministic amqplib channel handling, see https://github.com/squaremo/amqp.node/issues/388

## 2.9.0
### Fixed
- Randomising vhost connections on startup rather than on each connection request

## 2.8.0
### Fixed
- Workaround for non deterministic amqplib connection handling, see https://github.com/squaremo/amqp.node/issues/388

## 2.7.0
### Added
- AckOrNack emits/returns an error if an attempt was made to ack/nack a message using a closed channel
- Adjusting default connection_timeout and channel_max url parameters

## 2.6.0
### Added
- Exponential backoff for re-connections and channel re-subscriptions
- Fixed typo in deprecation warning

## 2.5.0
### Fixed
- Subscriber session could attempt to ack/nack messages using a closed channel. Leaving the channel open for 1 minute after cancelling subscription.

## 2.4.0
### Added
- Socket options can be specified in the vhost connection configuration. Connection timeout defaults to 1 minute.

## 2.3.2
### Updated
- Use self instead of this for code which called broker.nuke without binding context

## 2.3.1
### Updated
- Updated dependences

## 2.3.0
### Added
- Broker.unsubscribeAll to remove subscriptons. Mostly useful for automated tests

## 2.2.0
### Added
- Decorate inbound messages with originalVhost header

## 2.1.0
### Added
- Default publications and subscriptions are marked with an autoCreated flag

### Changed
- Default publications and subscriptions are are qualified with the vhost

### Deprecated
- Unqualified publications and subscriptions have been deprecated. A console.warn is logged once per subscription and publication but can be disabled by setting RASCAL_DISABLE_ALL_DEPRECATION_WARNINGS=true or RASCAL_DISABLE_UNQUALIFIED_NAME_DEPRECATION_WARNING=true

## 2.0.0
### Fixed
- Connection pool was leaking connections following a connection error. With a pool size of 1, this locked up all publishers
- Listening to close and error events caused multiple channels to be created which appears to result in an unknown delivery tag error. See https://github.com/squaremo/amqp.node/issues/271
- Incorrect documenation said to listen for invalid_content, but in reality the event was invalid_message. Now emitting invalid_message only if invalid_content is not handled.
- Fixed examples

## 1.4.1
### Fixed
- confirmPoolSize option as per https://github.com/guidesmiths/rascal/pull/19

## 1.4.0
### Added
- Listing to connection close events as per #18
- Fixed bug with configuration which caused vhost config errors to be masked

## 1.3.1
### Added
- Channel pooling (makes publishing much faster)

### Updated
- Dependencies

## 1.2.1
### Updated
- Used wrong argument in callback

## 1.2.0
### Added
- Workaround for https://github.com/guidesmiths/rascal/issues/17

## 1.1.0
### Added
- This changelog
- License
- Badges
- Upgrading dependencies

The format is based on [Keep a Changelog](http://keepachangelog.com/)
