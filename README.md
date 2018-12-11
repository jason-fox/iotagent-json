# FIWARE IoT Agent for a JSON-based Protocol

[![FIWARE IoT Agents](https://nexus.lab.fiware.org/static/badges/chapters/iot-agents.svg)](https://www.fiware.org/developers/catalogue/)
[![License: APGL](https://img.shields.io/github/license/telefonicaid/iotagent-json.svg)](https://opensource.org/licenses/AGPL-3.0)
[![Docker badge](https://img.shields.io/docker/pulls/fiware/iotagent-json.svg)](https://hub.docker.com/r/fiware/iotagent-json/)
[![Support badge](https://nexus.lab.fiware.org/repository/raw/public/badges/stackoverflow/iot-agents.svg)](https://stackoverflow.com/questions/tagged/fiware+iot)
<br/>
[![Documentation badge](https://img.shields.io/readthedocs/fiware-iotagent-json.svg)](http://fiware-iotagent-json.readthedocs.org/en/latest/?badge=latest)
![Status](https://nexus.lab.fiware.org/static/badges/statuses/iot-json.svg)

An Internet of Things Agent for a JSON based protocol (with
[AMQP](https://www.amqp.org/), [HTTP](https://www.w3.org/Protocols/) and
[MQTT](https://mqtt.org/) transports). This IoT Agent is designed to be a bridge
between [JSON](https://json.org/) and the
[NGSI](https://swagger.lab.fiware.org/?url=https://raw.githubusercontent.com/Fiware/specifications/master/OpenAPI/ngsiv2/ngsiv2-openapi.json)
interface of a context broker.

It is based on the
[IoT Agent Node.js Library](https://github.com/telefonicaid/iotagent-node-lib).
Further general information about the FIWARE IoT Agents framework, its
architecture and the common interaction model can be found in the library's
GitHub repository.

This project is part of [FIWARE](https://www.fiware.org/). For more information
check the FIWARE Catalogue entry for the
[IoT Agents](https://github.com/Fiware/catalogue/tree/master/iot-agents).

## Contents

-   [Background](#background)
-   [Install](#build--install)
-   [Usage](#usage)
-   [API](#api)
-   [Command Line Client](#command-line-client)
-   [Testing](#testing)
-   [Quality Assurance](#quality-assurance)
-   [License](#license)

## Background

This IoT Agent is designed to be a bridge between an MQTT/HTTP+JSON based
protocol and the FIWARE NGSI standard used in FIWARE. This project is based in
the Node.js IoT Agent library. More information about the IoT Agents can be
found within the library's
[GitHub repository](https://github.com/telefonicaid/iotagent-node-lib).

A quick way to get started is to read the
[Step by step Manual](./docs/stepbystep.md).

As is the case in any IoT Agent, this one follows the interaction model defined
in the
[Node.js IoT Agent Library](https://github.com/telefonicaid/iotagent-node-lib),
that is used for the implementation of the Northbound APIs. Information about
the IoTAgent's architecture can be found on that global repository. This
documentation will only address those features and characteristics that are
particular to the JSON IoTAgent.

If you want to contribute to the project, check out the
[Development section](#development) and the
[Contribution guidelines](./docs/contribution.md).

Additional information about operating the component can be found in the
[Operations: logs and alarms](docs/operations.md) document.

## Install

Information about how to install the JSON IoTAgent can be found at the
corresponding section of the
[Installation & Administration Guide](https://fiware-iotagent-json.readthedocs.io/en/latest/installationguide).

## Usage

Information about how to use the IoT Agent can be found in the
[User & Programmers Manual](https://fiware-iotagent-json.readthedocs.io/en/latest/stepbystep).

## API

Apiary reference for the Configuration API can be found
[here](http://docs.telefonicaiotiotagents.apiary.io/#reference/configuration-api)
More information about IoT Agents and their APIs can be found in the IoT Agent
Library [documentation](https://iotagent-node-lib.rtfd.io/).

## Command Line Client

The JSON IoT Agent comes with a client that can be used to test its features,
simulating a device. The client can be executed with the following command:

```console
bin/iotaJsonTester.js
```

This will show a prompt where commands can be issued to the MQTT broker. For a
list of the currently available commands type `help`.

The client loads a global configuration used for all the commands, containing
the host and port of the MQTT broker and the API Key and Device ID of the device
to simulate. This information can be changed with the `config` command.

In order to use any of the MQTT commands, you have to connect to the MQTT broker
first. If no connection is available, MQTT commands will show an error message
reminding you to connect.

The Command Line Client gets its default values from a config file in the root
of the project: `client-config.js`. This config file can be used to permanently
tune the MQTT broker parameters, or the default device ID and APIKey.

## Testing

[Mocha](http://visionmedia.github.io/mocha/) Test Runner + [Should.js](https://shouldjs.github.io/) Assertion Library.

The test environment is preconfigured to run BDD testing style.

Module mocking during testing can be done with
[proxyquire](https://github.com/thlorenz/proxyquire)

To run tests, type

```console
npm test
```

#### Requirements

All the tests are designed to test end to end scenarios, and there are some
requirements for its current execution:

-   Mosquitto v1.3.5 server running
-   MongoDB v3.x server running

#### Execution

To run tests, type

```console
grunt test
```

Tests reports can be used together with Jenkins to monitor project quality
metrics by means of TAP or XUnit plugins. To generate TAP report in
`report/test/unit_tests.tap`, type

```console
grunt test-report
```

## Quality Assurance

This project is part of [FIWARE](https://fiware.org/) and has been rated as
follows:

-   **Version Tested:**
    ![ ](https://img.shields.io/badge/dynamic/json.svg?label=Version&url=https://fiware.github.io/catalogue/json/iotagent_json.json&query=$.version&colorB=blue)
-   **Documentation:**
    ![ ](https://img.shields.io/badge/dynamic/json.svg?label=Completeness&url=https://fiware.github.io/catalogue/json/iotagent_json.json&query=$.docCompleteness&colorB=blue)
    ![ ](https://img.shields.io/badge/dynamic/json.svg?label=Usability&url=https://fiware.github.io/catalogue/json/iotagent_json.json&query=$.docSoundness&colorB=blue)
-   **Responsiveness:**
    ![ ](https://img.shields.io/badge/dynamic/json.svg?label=Time%20to%20Respond&url=https://fiware.github.io/catalogue/json/iotagent_json.json&query=$.timeToCharge&colorB=blue)
    ![ ](https://img.shields.io/badge/dynamic/json.svg?label=Time%20to%20Fix&url=https://fiware.github.io/catalogue/json/iotagent_json.json&query=$.timeToFix&colorB=blue)
-   **FIWARE Testing:**
    ![ ](https://img.shields.io/badge/dynamic/json.svg?label=Tests%20Passed&url=https://fiware.github.io/catalogue/json/iotagent_json.json&query=$.failureRate&colorB=blue)
    ![ ](https://img.shields.io/badge/dynamic/json.svg?label=Scalability&url=https://fiware.github.io/catalogue/json/iotagent_json.json&query=$.scalability&colorB=blue)
    ![ ](https://img.shields.io/badge/dynamic/json.svg?label=Performance&url=https://fiware.github.io/catalogue/json/iotagent_json.json&query=$.performance&colorB=blue)
    ![ ](https://img.shields.io/badge/dynamic/json.svg?label=Stability&url=https://fiware.github.io/catalogue/json/iotagent_json.json&query=$.stability&colorB=blue)

---

## Licence

The IoT Agent for JSON is licensed under Affero General Public License (GPL)
version 3.

© 2018 Telefonica Investigación y Desarrollo, S.A.U
