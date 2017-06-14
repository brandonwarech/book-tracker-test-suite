# whisk-mocha

## Summary

This repository holds sample code demonstrating a pattern for unit testing [Apache OpenWhisk](http://openwhisk.org) node.js actions with [mocha](https://mochajs.org/).



This pattern shows how to write one mocha suite that can be used to unit test actions either 1) locally on your machine, or 2) remotely on OpenWhisk.   The code uses a trick so that you can re-use the same test suite in both contexts.   So, with this pattern, you can develop and test your actions locally; when ready, you can deploy them to the cloud and use the same test suite to exercise the actions in the cloud.

## How it works

The sample code shows how to use the [Adapter](https://en.wikipedia.org/wiki/Adapter_pattern) design pattern to abstract local and cloud-hosted actions behind a common interface.   The code uses a simple introspective utility in Javascript to build the adapter.

## Instructions

The repository contains the following files:
* [hello.js](https://github.com/sjfink/whisk-mocha/blob/master/hello.js) a simple Node.js OpenWhisk action
* [test.js](https://github.com/sjfink/whisk-mocha/blob/master/test.js) a `mocha` test suite for the hello actions
* [driver.sh](https://github.com/sjfink/whisk-mocha/blob/master/driver.sh) shell script to drive the example.

### Prerequisites

This has been tested on MacOSX and will probably work on Linux.  You will need `bash`, `node` and `mocha`.

This assumes you have installed the `wsk` command-line.  For IBM Bluemix, get it [here](https://console.ng.bluemix.net/openwhisk/learn/cli).  

### Steps

1. Install the action and required `npm` packages:
```
./driver.sh --install
```

2. Run unit tests locally
```
./driver.sh --testLocal
```

3. Run unit tests against OpenWhisk
```
./driver.sh --testOW
```

4. Uninstall the action and clean up
```
./driver.sh --clean
```
