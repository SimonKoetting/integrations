# Trend Micro Vision One

## Overview

The [Trend Micro Vision One](https://www.trendmicro.com/en_in/business/products/detection-response.html) integration allows you to monitor Alert, Audit, Detection and Telemetry activity. Trend Micro Vision One refers to the ability to do detection and response across email, endpoints, servers, cloud workloads, and networks via a single Trend Micro Vision One platform or the managed Trend Micro Vision One service.

Use the Trend Micro Vision One integration to collects and parses data from the REST APIs. Then visualize that data in Kibana.

## Data streams

The Trend Micro Vision One integration collects logs for four types of events: Alert, Audit, Detection and Telemetry.

**Alert** Displays information about workbench alerts. See more details in the doc [here](https://automation.trendmicro.com/xdr/api-v3#tag/Workbench/paths/~1v3.0~1workbench~1alerts/get).

**Audit** Displays log entries that match the specified search criteria. See more details in the doc [here](https://automation.trendmicro.com/xdr/api-v3#tag/Audit-Logs).

**Detection** Displays search results from the Detection Data source. See more details in the doc [here](https://automation.trendmicro.com/xdr/api-v3#tag/Search/paths/~1v3.0~1search~1detections/get).

**Telemetry** Displays telemetry events from the Datalake Pipeline API. See more details in the doc [here](https://automation.trendmicro.com/xdr/api-v3/#tag/Datalake-Pipeline).


## Requirements

You need Elasticsearch for storing and searching your data and Kibana for visualizing and managing it. You can use our hosted Elasticsearch Service on Elastic Cloud, which is recommended, or self-manage the Elastic Stack on your hardware.

This module has been tested against `Trend Micro Vision One API version 3.0`.

**Note:** The API key generated by a user expires one year after being generated.

**Important**: For the Telemetry data stream, which uses the Datalake Pipeline APIs, you need to allocate Trend Vision One credits for Data Transfer. For more information, see [Credit requirements for Trend Vision One solutions, capabilities and services > Data Transfer](https://docs.trendmicro.com/en-us/documentation/article/trend-vision-one-credit-req-for-apps-services#GUID-001E41E3-6F8A-499E-85E5-14A3DBD67C6C__section_zxw_5k2_qbc).

## Setup

### To collect data from Trend Micro Vision One APIs, the user must have an API key. To create an API key follow the below steps:

1. Log on to the Trend Micro Vision One console.
2. On the Trend Vision One console, go to **Administration -> API Keys**.
3. Generate a new API Key. Click **Add API key**. Specify the settings of the new API key.
    - **Name**: A meaningful name that can help you identify the API key.
    - **Role**: The user role assigned to the key. API keys can use either predefined or custom user roles. Custom roles can be created by navigating to **Administration -> User Roles -> Add Role**. The role must have appropriate API access permission to fetch relevant data. The following table outlines the access permissions to apps and features needed to fetch relevant data from Trend Vision API.

        | Datastream   | Section                                                      | Permissions                                        |
        |--------------|--------------------------------------------------------------|----------------------------------------------------|
        | Alert        | Platform Capabilities > XDR Threat Investigation > Workbench | `View, filter, and search`.                        |
        | Audit        | Settings > Administration > Audit Logs                       | `View, filter, and search`, `Export and Download`. |
        | Detection    | Platform Capabilities > XDR Threat Investigation > Search    | `View, filter, and search`.                        |
        | Telemetry    | Platform Capabilities > XDR Threat Investigation > Search    | `View, filter, and search`.                        |

        Refer to [Account Role Permissions](https://automation.trendmicro.com/xdr/Guides/Authentication) for more details.

    - **Expiration time**: The time the API key remains valid. By default, API keys expire one year after creation. However, a master administrator can delete and re-generate API keys at any time.
    - **Status**: Whether the API key is enabled.
    - **Details**: Extra information about the API key.

    Click **Add**.
4. Copy the value of the API key.

Refer to [First steps toward using the APIs](https://automation.trendmicro.com/xdr/Guides/First-steps-toward-using-the-APIs) for more details on setting up an API key.

Confirm that you have allocated credits for Data Transfer if you are activating the Telemetry data stream.

When the Telemetry data stream starts for the first time it will use the Datalake Pipeline API to bind all telemetry data types to a new pipeline with a distinctive description. If a pipeline with that description already exists, it will be reused. It will never delete the pipeline, so if you stop using the integration, that pipeline should be removed manually.

## Logs Reference

### alert

This is the `alert` dataset.

#### Example

{{event "alert"}}

{{fields "alert"}}

### audit

This is the `audit` dataset.

#### Example

{{event "audit"}}

{{fields "audit"}}

### detection

This is the `detection` dataset.

#### Example

{{event "detection"}}

{{fields "detection"}}

### telemetry

This is the `telemetry` dataset.

#### Example

{{event "telemetry"}}

{{fields "telemetry"}}
