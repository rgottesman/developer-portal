# Table of Contents {#table-of-contents .TOC-Heading}

[How the Surfsight API works 1](#how-the-surfsight-api-works)

[Surfsight concepts 2](#surfsight-concepts)

[REST APIs 2](#rest-apis)

[Webhooks 3](#webhooks)

[What can you use webhooks for? 3](#what-can-you-use-webhooks-for)

[How are our webhooks secured? 3](#how-are-our-webhooks-secured)

[Tokens & credentials 3](#tokens-credentials)

[What credential options are there?
3](#what-credential-options-are-there)

[Integrating by using our API 4](#integrating-by-using-our-api)

[What can you do with our API? 4](#what-can-you-do-with-our-api)

[Call structure 6](#call-structure)

[Authentication 6](#authentication)

[Basic authentication 6](#basic-authentication)

[Organization authentication 7](#organization-authentication)

[Guides 8](#guides)

[How partners add a new customer 8](#how-partners-add-a-new-customer)

[Authenticate 9](#authenticate)

[Create organizations 10](#create-organizations)

[Create groups 10](#create-groups)

[Add devices 10](#add-devices)

[Add users 11](#add-users)

[API changelog 11](#api-changelog)

[Terminology 11](#terminology)

# How the Surfsight API works

Our API is based on [REST APIs](#rest-apis) and uses
[webhooks](#webhooks) to let you know when events occur. To leverage our
API successfully, it\'s important to understand certain
[concepts](#surfsight-concepts) and to understand [tokens and
credentials](#tokens-credentials).

## Surfsight concepts

Surfsight enables you to manage your fleets smoothly by leveraging a
hierarchical structure for each account; you can build your hierarchy
for device management, including division of devices by organizations
(parents) and by groups (children).

The following terms can help you understand the Surfsight API:

-   **Fleet** - your set of vehicles, each with at least one device
    installed

-   **Device** - a video telematics device, such as the AI-12 dashcam.

-   **Camera** - a camera connected to the device, such as the
    road-facing camera, the in-cabin camera and auxiliary cameras

-   **Auxiliary cameras** - camera that can be installed on different
    spots of a vehicle to enable tracking of other perspectives during
    trips. Each auxiliary camera is associated with a single device

-   **Organization** - organizations are the largest categorization for
    fleets and their devices; each organization can contain any number
    of groups and devices

-   **Group** - groups are the second largest categorization for fleets
    and their devices; each group can contain any number of devices.
    Each group is part of an organization

-   **Recordings** - video of trips from all cameras associated with a
    device (the road-facing camera, the in-cabin camera, and any
    auxiliary cameras). The video is saved to the SD card and uploaded
    to the cloud

-   **Events** - video of events from all cameras associated with a
    device (the road-facing camera, the in-cabin camera, and any
    auxiliary cameras). The video is saved to the SD card and uploaded
    to the cloud. Events are any of a number of risky incidents that can
    occur during a trip, such as acceleration, violent turns, or
    distracted driving. Events can be configured to upload as text,
    snapshots, or videos. Video events capture 5 seconds before and
    after the event occurs. The data tracked for each event includes the
    type of event, the date and time of the event, the location of the
    event, and the speed of the vehicle during the event

-   **Live streaming** - live video from all cameras associated with a
    device (the road-facing camera, the in-cabin camera, and any
    auxiliary cameras). Live video can be streamed directly from the
    device, from the cloud, or through the API

## REST APIs

An API (Application Programming Interface) enables programs to talk to
each other. REST (Representational State Transfer) APIs are APIs that
use HTTP requests at a predefined set of URLs.

These URLs represent content accessed at that location, which can be
returned as JSON, HTML, audio files, or images. Resources usually have
one or more methods that can be performed on them over HTTP,
like GET, POST, PUT, and DELETE. In general, use GET to receive
resources, POST to create resources, PUT to update resources, and DELETE
to remove resources.

Surfsight provides many REST APIs for receiving information from your
devices, updating the settings of your devices, adding new
organizations, removing users, and more. The Surfsight API has two
regions of service:

-   North America - api-prod.surfsight.net

-   Europe - api.de.surfsight.net

## Webhooks

Webhooks are automated messages sent from apps when an event occurs.
They contain data and commands sent over HTTP.

Surfsight makes an HTTP request to the URL you configure for your
webhook. This request contains GPS data or data about events, often with
snapshots or videos attached.

### What can you use webhooks for?

Surfsight uses webhooks to send you:

-   event notifications

-   GPS data

### How are our webhooks secured?

Webhooks are secured through anonymity - every user gets a unique,
random URL to send webhook data to.

For extra security, all webhook information sent by Surfsight to your
application contains an additional header attribute:
**X-Surfsight-Signature**. The signature is created using the
destination URL, the ssoSecret of your organization, and the content of
the request. The signature should appear similar to:
29c4198c5e3da799887deaf0b0450bac8880efc0769cb79b97138ce9888a4308c7211415879152fdc4a14933c77cd4d531e71a29008214360ce340ccf49b87c8.

## Tokens & credentials

To start using the Surfsight API, you need to first authenticate
yourself. The Surfsight API uses Bearer authentication and you receive
an authentication token. This process is detailed in [Basic
authentication](#basic-authentication).

This token gives you access to the API operations according to your
role, as described in [What credential options are
there?](#what-credential-options-are-there). If you make a call using an
API operation you don\'t have access to, an error is returned.

### What credential options are there?

Your authentication token gives you access to the API operations
according to your role and its credentials. The different credentials
are described in the following table::

+----------+-----------------------------------------------------------+
| Role     | Credentials                                               |
+==========+===========================================================+
| Reseller | Reseller partners can create organizations, s, and        |
| partner  | reseller partner contacts. They can make any calls        |
|          | related to organizations and reseller partners.           |
|          | Additionally, they can make calls related to a specific   |
|          | organization, such as adding devices or modifying events. |
|          |                                                           |
|          | Reseller partners can also create a token with [admin     |
|          | credentials](#sectionidm4555670282940832575328148006)     |
|          | that is valid for twenty-four hours to authenticate any   |
|          | calls sent during that time for a specific organization.  |
|          | They can give this token to others to use, without having |
|          | to create a permanent user with admin credentials. For    |
|          | more information about this token, see [Organization      |
|          | authentication](#organization-authentication).            |
+----------+-----------------------------------------------------------+
|          | s can create organizations and reseller partner contacts. |
|          | They can make any calls related to organizations and      |
|          | reseller partners. Additionally, they can make calls      |
|          | related to a specific organization, such as adding        |
|          | devices or modifying events.                              |
+----------+-----------------------------------------------------------+
| Admin    | Administrators can make calls related to a specific       |
|          | organization, such as adding devices or modifying events. |
+----------+-----------------------------------------------------------+
| Su       | Supervisors have the same credentials as an               |
| pervisor | administrator, but cannot add, modify or remove users.    |
+----------+-----------------------------------------------------------+
| User     | Users have the came credentials as a supervisor, but      |
|          | cannot add new devices or create new groups.              |
+----------+-----------------------------------------------------------+
| R        | Restricted users are defined in the system but cannot     |
| estriced | make any calls.                                           |
+----------+-----------------------------------------------------------+

# Integrating by using our API

You can integrate with the Surfsight API and [make
calls](#what-can-you-do-with-our-api) that manage your devices and track
events. These calls need to be structured a specific way, as described
in [Call structure](#call-structure).

## What can you do with our API?

The Surfsight API enables you to manage devices and track events by
making calls using the following endpoints:

+--------------+-------------------------+-----------------------------+
| Name         | Description             | Endpoints                   |
+==============+=========================+=============================+
| Alarms       | Receive alarms reports, | /alarms                     |
|              | manage report email     |                             |
|              | recipients, and manage  |                             |
|              | alarms.                 |                             |
+--------------+-------------------------+-----------------------------+
| Audit logs   | Receive your            | /audit-logs                 |
|              | organization audit      |                             |
|              | logs.                   |                             |
+--------------+-------------------------+-----------------------------+
| Au           | Authenticate yourself   | /authenticate               |
| thentication | to access the Surfsight |                             |
|              | API.                    |                             |
+--------------+-------------------------+-----------------------------+
| Device       | Manage your device      | -   /devices/{imei}         |
| operations   | operations, such as     |                             |
|              | formatting SD cards and | -   /or                     |
|              | receiving data usage.   | ganizations/{orgId}/devices |
+--------------+-------------------------+-----------------------------+
| Devices      | Manage your devices and | -   /devices/{imei}         |
|              | receive data about your |                             |
|              | devices, such as a      | -   /organizations/{orgId}  |
|              | device\'s settings or   |                             |
|              | active cameras.         |                             |
+--------------+-------------------------+-----------------------------+
| Events       | Configure event         | /devices/{imei}             |
|              | settings and receive    |                             |
|              | data about your events, |                             |
|              | such as event settings  |                             |
|              | or an event\'s details. |                             |
+--------------+-------------------------+-----------------------------+
| Geofences    | Set geofences and       | /devices/{imei}/geofences   |
|              | receive a list of a     |                             |
|              | device\'s geofences.    |                             |
+--------------+-------------------------+-----------------------------+
| Groups       | Create and manage       | /o                          |
|              | groups.                 | rganizations/{orgId}/groups |
+--------------+-------------------------+-----------------------------+
| Health       | Receive alarms reports  | -   /device-health          |
|              | and manage report email |                             |
|              | recipients.             | -   /recipients/health      |
+--------------+-------------------------+-----------------------------+
| O            | Create and manage       | /organizations              |
| rganizations | organizations.          |                             |
+--------------+-------------------------+-----------------------------+
| Partner      | Receive your            | /part                       |
| operation    | operational statistics. | ners/operational-statistics |
| statistics   | Only partners can make  |                             |
|              | these calls.            |                             |
+--------------+-------------------------+-----------------------------+
| Partners     | Manage your partner     | /partners/{pernterId}       |
|              | contacts.               |                             |
+--------------+-------------------------+-----------------------------+
| Recordings   | Receive data about      | /devices/{imei}             |
|              | recordings availability |                             |
|              | for a device\'s cameras |                             |
|              | and snapshots of a      |                             |
|              | camera\'s current view. |                             |
+--------------+-------------------------+-----------------------------+
| Streaming    | Prepare live streaming  | /d                          |
|              | from a device.          | evices/{imei}/connect-media |
+--------------+-------------------------+-----------------------------+
| Telemetry    | Receive telemetry data  | /devices/{imei}             |
|              | from a device or        |                             |
|              | camera.                 |                             |
+--------------+-------------------------+-----------------------------+
| Users        | Manage users.           | /                           |
|              |                         | organizations/{orgId}/users |
+--------------+-------------------------+-----------------------------+
| Virtual      | Generate virtual        | /d                          |
| events       | events.                 | evices/{imie}/virtual-event |
+--------------+-------------------------+-----------------------------+
| Webhooks     | Mange your webhooks     | /org                        |
|              | subscriptions.          | anizations/{orgId}/webhooks |
+--------------+-------------------------+-----------------------------+

These endpoints are detailed in the
[/document/preview/25336#UUID98c720077150bae523489d0a67826391](/document/preview/25336#UUID98c720077150bae523489d0a67826391).API
reference

## Call structure

Your call to the Surfsight API should appear similar to:

    curl --request {httpMethod} 'https://api-prod.surfsight.net/{apiVersion}/{apiEndpoint}'
    --header 'Authorization: {token}'

The base URL is https://api-prod.surfsight.net/{apiVersion} for North
America and https://api.de.surfsight.net/{apiVersion} for Europe, with
v2 being the default API version.

The API call includes the following:

  ---------------------------------------------------------------------------------------
  Component       Description                 Example                          Location
  --------------- --------------------------- -------------------------------- ----------
  HTTP method     The action you want to      GET                              request
                  perform                                                      

  URL             The Surfsight API URL       https://api-prod.surfsight.net   request

  API version     The version of the          v2                               request
                  Surfsight API you are                                        
                  calling                                                      

  API endpoint    The API endpoint you want   /devices/{imei}/events           request
                  to reach                                                     

  Authorization   The [authentication         1234567                          header
                  token](#N1622535612653) in                                   
                  the Authorization header of                                  
                  your call                                                    
  ---------------------------------------------------------------------------------------

# Authentication

With our API you can authenticate in several ways:

-   [Basic authentication](#basic-authentication)

-   [Single sign on (SSO) authentication](#organization-authentication)

## Basic authentication

Surfsight API uses Bearer authentication (also known as token
authentication). The server generates a bearer token in response to a
login request. The client provides this token in the **Authorization**
header when making further requests.

    --header 'Authorization: ImahFWLZWFdD8VVcUtIED2YuOjPFlZpldQTE5tUqKdv'

You need an email address and password to get a token. When beginning
your partnership with Surfsight, we send you an email containing this
information.

> **Note**
>
> Every company can request up to nineteen additional usernames.

**To receive an authentication token:**

Make the **POST /authentication** call. Enter the email address and
password you received in an email from a Surfsight agent in the request
body and an authentication token is returned.

    curl --request POST 'https://api-prod.surfsight.net/v2/authentication'
    --header 'Content-Type: application/json'
    --data-raw '{

      "email": "email@email.com",
      "password": "123Abcd!"
    }'

> **Note**
>
> The token that is returned is valid for twenty-four hours.

## Organization authentication

Partners can create an admin token that is valid for twenty-four hours
to authenticate any requests sent during that time for a specific
organization.

**To generate an admin token for an organization:**

1.  Create an organization using the **POST /organizations** call.

-   curl --request POST https://api-prod.surfsight.net/v2/organizations
        --header 'Content-Type: application/json'
        --header 'Authorization: {token}'
        --data-raw '{

          "name": "organization 1"
        }'

    > **Note**

    > This API call must be made by a user who is defined as a partner
    > in the system. If you do not have partner permission credentials
    > please reach out to your technical account manager to receive
    > partner API credentials.

    The API request returns two keys: **ssoSecret** and
    **organizationld**.

    > **Caution**

    > Securely store these key values on your backend database. These
    > keys are not stored on the Surfsight system.

2.  Create a JWT token. You can use the following site:
    <https://jwt.io/>.

-   ![](media/image1.png){width="4.7573797025371825in"
    height="3.044722222222222in"}

    The following parameters must be set:

    -   current timestamp

    -   ssoSecret

    -   organizationId

    > **Note**

    > The JWT token is valid for fifteen minutes. It is encrypted with
    > HS256 and sends private claims.

3.  Request an admin token with the **GET /organizations/sso** call.

-   Provide your JWT token in the authorization header.

        curl --request GET https://api-prod.surfsight.net/v2/organizations/sso
        --header 'Content-Type: application/json'
        --header 'Authorization: {JWT token}'

    > **Note**

    > The admin token that is returned is valid for twenty-four hours.

# Guides

## How partners add a new customer

Make sure you received an email with an email address and password to
access the Partner Portal and API.

Surfsight enables you to manage your fleets smoothly by leveraging a
hierarchical structure for each account; you can build your hierarchy
for device management, including division of devices by organizations
(parents) and by groups (children).

When a new customer signs up with you for Surfsight services, we
recommend that you first talk with them about possible ways to group and
manage their devices based on these options. The structure they choose
will most likely depend on the size and number of fleets they\'re
managing, in addition to any other relevant organizational decisions.

Once you\'ve mapped out fleets and their devices to Surfsight
organizations and groups, you can start creating those organizations and
groups for the account and then also add users and devices.

The rest of this guide shows you how to use the Surfsight API, to
quickly perform the following steps:

1.  [Authenticate](#authenticate) yourself.

2.  [Create organizations](#create-organizations).

3.  [Create groups](#create-groups).

4.  [Add devices to your organizations](#add-devices).

5.  [Add users to your organizations](#add-users).

> **Note**
>
> For more information about the different API calls, take a look at our
> [reference
> guide](/document/preview/25336#UUID98c720077150bae523489d0a67826391).API
> reference

### Authenticate

Authenticate yourself with the **GET /authentication** call.

Surfsight API uses Bearer authentication (also known as token
authentication). The server generates a bearer token in response to a
login request. The client provides this token in the **Authorization**
header when making further requests.

    --header 'Authorization: ImahFWLZWFdD8VVcUtIED2YuOjPFlZpldQTE5tUqKdv'

You need an email address and password to get a token. When beginning
your partnership with Surfsight, we send you an email containing this
information.

> **Note**
>
> Every company can request up to nineteen additional usernames.

**To receive an authentication token:**

Make the **POST /authentication** call. Enter the email address and
password you received in an email from a Surfsight agent in the request
body and an authentication token is returned.

    curl --request POST 'https://api-prod.surfsight.net/v2/authentication'
    --header 'Content-Type: application/json'
    --data-raw '{

      "email": "email@email.com",
      "password": "123Abcd!"
    }'

> **Note**
>
> The token that is returned is valid for twenty-four hours.

### Create organizations

Create organizations with the **POST /organizations** call.

    curl --request POST https://api-prod.surfsight.net/v2/organizations
    --header 'Content-Type: application/json'
    --header 'Authorization: {token}'
    --data-raw '{

      "name": "Missouri fleet"
    }'

> **Note**
>
> The organizationID is returned in this call. Save this ID to use in
> other calls. You can also get the ID again from
> the** GET /organizations** call.

### Create groups

Create groups with the **POST /organizations/{orgId}/groups** call.

    curl --request POST https://api-prod.surfsight.net/v2/organizations/{orgId}/groups
    --header 'Content-Type: application/json'
    --header 'Authorization: {token}'
    --data-raw '{

      "name": "St. Louis fleet"
    }'

### Add devices

Add devices to your organizations:

-   for individual devices - with the
    **POST /organizations/{orgId}/devices** call

```{=html}
<!-- -->
```
-   curl --request POST https://api-prod.surfsight.net/v2/organizations/{orgId}/devices
        --header 'Content-Type: application/json'
        --header 'Authorization: {token}'
        --data-raw '{

          "imei": "357660101000198",
          "name": "Harry's car",
          "groupId": 32
        }'

```{=html}
<!-- -->
```
-   for multiple devices at once - with the
    **POST /organizations/{orgId}/bulk-devices** call

```{=html}
<!-- -->
```
-   curl --request POST https://api-prod.surfsight.net/v2/organizations/{orgId}/bulk-devices
        --header 'Content-Type: application/json'
        --header 'Authorization: {token}'
        --data-raw '[

          {
            "imei": "357660101000198",
            "name": "Harry's car",
            "groupId": 32
          },
          {
            "imei": "357660101000276",
            "name": "Ginny's car",
            "groupId": 26
          }
        ]'

    A list of accepted and rejected devices by IMEI number is returned.

### Add users

Add users to your organizations with the
**POST /organizations/{orgId}/users** call.

When creating a user, you also assign their role: restricted, user,
administrator, or supervisor. For details about each role\'s
credentials, see [Tokens & credentials](#tokens-credentials).

    curl --request POST https://api-prod.surfsight.net/v2/organizations/{orgId}/users
    --header 'Content-Type: application/json'
    --header 'Authorization: {token}'
    --data-raw '{

      "email": "email@email.com",
      "password": "123Abcd!",
      "role": "user"
    }'

# API changelog

# Terminology

# 

auxiliary camera

A camera that can be installed on different spots of a vehicle to enable
tracking of other perspectives during trips. Each auxiliary camera is
associated with a single device.

camera

A camera connected to the device, such as the road-facing camera, the
in-cabin camera and auxiliary cameras.

device

A video telematics device, such as the AI-12 dashcam.

device configuration

You can configure your device settings. These settings include:

-   distractedDriver - enable or disable in-cabin audio and visual
    alerts when distracted driving events, such as cell phone usage,
    eating and drinking, or smoking, occur

-   textOverlay - enable or disable text overlay in video recordings and
    video events

-   inCabinCameraRecording - enable or disable in-cabin recordings. The
    distracted driver feature works whether or not the recordings are on

-   driverPosition - set the driver seat location - the left or right
    side of the vehicle. Must be set correctly for the distracted driver
    setting to work properly

-   speedUnits - set the units used for speed measurement to miles per
    hour or kilometers per hour

-   audioAlarms - enable or disable audio alarms from the device for
    dangerous and distracted driving events

-   notifyLiveStreaming - enable or disable on-screen text notifications
    when someone is viewing live video of the device

-   adminPIN - set the admin PIN

-   driverPIN - set the driver PIN

-   brightness - set the screen brightness to a value between 0 and 255.

-   dateTimeUnits - set the units used for date and time to \'us\' for
    US units or \'eu\' for metric units

-   voiceRecording - enable or disable recording audio in the vehicle

-   standby - set the time period after which the camera enters standby
    mode once the vehicle stops moving, between 1 and 60 minutes

-   hotspot - enable or disable internet access via the device hotspot

-   privacy - the privacy settings, which include:

    -   gpsEnabled - enable or disable the GPS tracking

    -   mvaiEnabled - enable or disable MVAI, machine vision and
        artificial intelligence, which identifies distracted driving

    -   cameras - enable or disable recordings and events for specific
        cameras

event

Video of events from all cameras associated with a device (the
road-facing camera, the in-cabin camera, and any auxiliary cameras). The
video is saved to the SD card and uploaded to the cloud. Events are any
of a number of risky incidents that can occur during a trip, such as
acceleration, violent turns, or distracted driving. Events can be
configured to upload as text, snapshots, or videos. Video events capture
5 seconds before and after the event occurs. The data tracked for each
event includes the type of event, the date and time of the event, the
location of the event, and the speed of the vehicle during the event.

fleet

A number of vehicles, each with a device installed.

group

Devices can be consolidated within a single group. Once you configure a
group and associate any devices, you can then centrally manage those
devices at the group level.

IMEI

The unique identifier of the device.

The IMEI number can be found on the sticker on the dashcam itself or on
the back of the dashcam box.

live stream

Live video from all cameras associated with a device (the road-facing
camera, the in-cabin camera, and any auxiliary cameras). Live video can
be streamed directly from the device, from the cloud, or through the
API.

organization

Individual devices and groups can be consolidated within a single
organization. Once you configure an organization and associate any
devices or groups, you can then centrally manage those devices and
groups at the organization level.

recording

Video of trips from all cameras associated with a device (the
road-facing camera, the in-cabin camera, and any auxiliary cameras). The
video is saved to the SD card and uploaded to the cloud.

REST API

REST APIs allow for interaction with RESTful web services. In RESTful
web services, requests made to a resource\'s URI receive a
response formatted in HTML, XML, JSON, or some other format. REST APIs
are defined in the [OpenAPIv3 definition
file](https://swagger.io/specification/). 

webhooks

Receive real-time event notifications from your devices to a URL of your
choice.

webRTC

Web real-time communication. This open source project helps to embed
real-time voice, text and video in Web browsers without using plugins.
This simplifies communication and improves user experience.
