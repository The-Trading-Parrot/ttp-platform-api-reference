# TTP - Platform API Reference
Official reference repo for the TTP public APIs.

## Overview

The platform API empowers developers to offer advanced services to the members of [TheTradingParrot](https://thetradingparrot.com) community that will enroll through the [Services Dashboard](https://services-dashboard.thetradingparrot.com).

If you're a developer and you want to offer a service to the community, please contact us at thetradingparrot AT gmail DOT com.

This document is intended to provide a general guidance on how to consume our APIs. The full documentation is available at **[TheTradingParrot Development API with Swagger](https://api.thetradingparrot.com/api-docs/)** .

## Authentication

The APIs serve data from the user that have subscribed to the community, and OAuth2 is used as a way to authorize and revoke access to your services and user data.

For details on how to authorize and authenticate an user, please consult the [Authentication](docs/Authentication.md) page.

All requests, unless otherwise specified, must be performed with the HTTP bearer authentication, by passing the `Authorization: Bearer <access_token>` in the headers.

### Client

Clients must address requests to `api.thetradingparrot.com` using HTTPS and specify the `Accept: application/vnd.thetradingparrot+json;version=1.0` Accept header. 

The current API version is **1.0**. 

### Rate limits

The endpoints are currently not rate limited but we reserve the rights to introduce changes in the upcoming releases.

### Response and errors

The error and response status are documented in the Swagger API page.

---

Copyright © - TTP BOTS LTD 2021
