# Webhooks

> ActiGraph's CentrePoint Webhook system is inspired by GitHub's Webhook API. There are many similarities if you are familiar with their system.

- [Overview](#overview)
- [Managing Webhooks](#Managing-webhooks)
- [Securing Webhooks](#securing-webhooks)
- [Validating Webhooks](#validating-webhooks)
- [Events](#events)
- [Open Firewall Access](#open-firewall-access)


## CentrePoint Integration Guide
-------------------
To view all options/alternatives to integrate with the CentrePoint System, refer to the [CentrePoint Integration Guide](https://github.com/actigraph/CentrePointIntegrationGuide#centrepoint-system-integration-guide).

## Overview

Webhooks allow you to build or set up integrations which subscribe to certain events on ActiGraph's CentrePoint ecosystem. When one of those events is triggered, the system will send a HTTP POST request containing event data to the webhook's configured URL. Webhooks can be used to update an external system or just for simple notifications.

Webhooks are configured per study configuration. Once configured, they will be triggered each time one or more subscribed events occurs on that Study. 

## Managing Webhooks

Webhooks are managed in the [CentrePoint Web Portal](https://studyadmin.actigraphcorp.com). Refer to [Managing Webhooks](managing_webhooks.md) for more information.

## Securing Webhooks

The CentrePoint system provides various methods for authenticating outbound webhooks including [BASIC Auth](https://en.wikipedia.org/wiki/Basic_access_authentication) and Keyed-Hash (HMAC). Refer to [Securing Webhooks](securing_webhooks.md) for more information.

## Validating Webhooks

Before any events can be sent to the Target URL for a webhook, the webhook needs to pass a validation process. The main purpose of this validation process is for ActiGraph to verify the owner of the Target URL. The verification process involves a validation code being sent to the Target URL, and your endpoint echoing back that same code. Refer to [Validating Webhooks](validating_webhooks.md) for more information.


## Events

Events are what you wish to subscribe to in order to receive notifications once they are triggered. Events correspond to a certain set of actions that can happen to your Study. For example, if you subscribe to the `upload` event you'll receive some details pertaining to any uploads to subjects that are managed under the Study (when the upload started, completes or encounters an error).

Available events are:

1. `raw processing complete` *Event triggered upon processing completion of RAW sub-second data in the CentrePoint Version 3 System. This event can be used to denote when RAW data files are available to be retrieved in the CentrePoint (V3) API (via Data Retrieval request).* This will be the first event in the data processing pipeline from an upload-sync.

2. `data retrieval complete` *Event triggered upon the completion of data retrieval request in the CentrePoint V3 API. This event can be used to know when RAW data files are available to be downloaded (from a previous data retrieval request) in the CentrePoint (V3) API.*

3. `upload` *Relates to events for the processing (or ingestion) of a given upload-sync. This event is triggered when CentrePoint processes an upload. There's three variations of the event: started (denotes that processing has started), completed (denotes processing has completed), and error (denotes an error occurred during the upload processing)*. This is the final event in the data processing pipeline from an upload-sync.

## Open Firewall Access 

In some scenarios, external systems receiving webhooks from ActiGraph may be behind a reverse-proxy with firewall enforcement. Here are the list of IPs that will need to be whitelisted in order to receive in-bound webhook requests from ActiGraph


- 13.82.60.74
- 40.114.106.25
- 40.114.109.196
- 40.87.40.14
- 40.87.44.79
- 40.87.47.202
- 40.87.41.144
- 40.87.47.137
- 13.68.136.18
