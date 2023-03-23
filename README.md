# Webhook Server

|           |                                                                                     |
| --------- | ----------------------------------------------------------------------------------- |
| Name      | Webhook Server                                                                      |
| Version   | v1.0.0                                                                              |
| DockerHub | [weevenetwork/webhook-server](https://hub.docker.com/r/weevenetwork/webhook-server) |
| authors   | Jakub Grzelak                                                                       |

## Table of Content

- [Webhook Server](#webhook-server)
  - [Table of Content](#table-of-content)
  - [Description](#description)
  - [Environment Variables](#environment-variables)
    - [Module Specific](#module-specific)
    - [Set by the weeve Agent on the edge-node](#set-by-the-weeve-agent-on-the-edge-node)
  - [Dependencies](#dependencies)
  - [Input](#input)
  - [Output](#output)

## Description

This module creates a webhook server. it accepts and processes ingress from HTTP POST/POST/PATCH requests.

NOTE: currently only IPv4 is supported.

## Environment Variables

### Module Specific

The following module configurations can be provided in a data service designer section on weeve platform:

| Environment Variables | type   | Description                       |
| --------------------- | ------ | --------------------------------- |
| HOST_PORT             | string | Port on which the server will run |


### Set by the weeve Agent on the edge-node

Other features required for establishing the inter-container communication between modules in a data service are set by weeve agent.

| Environment Variables | type   | Description                                                                                          |
| --------------------- | ------ | ---------------------------------------------------------------------------------------------------- |
| MODULE_NAME           | string | Name of the module                                                                                   |
| MODULE_TYPE           | string | Type of the module (Input, Processing, Output)                                                       |
| EGRESS_URLS           | string | HTTP ReST endpoint for the next module                                                               |
| LOG_LEVEL             | string | Allowed log levels: DEBUG, INFO, WARNING, ERROR, CRITICAL. Refer to `logging` package documentation. |

## Dependencies

```txt
bottle
requests
```

## Input

HTTP ReST POST/POST/PATCH request with request-body

## Output

Output of this module is JSON body the same as the JSON body received from HTTP POST request.
