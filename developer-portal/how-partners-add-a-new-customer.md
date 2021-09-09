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
> [reference guide]().

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

        curl --request POST https://api-prod.surfsight.net/v2/organizations/{orgId}/devices
        --header 'Content-Type: application/json'
        --header 'Authorization: {token}'
        --data-raw '{

            "imei": "357660101000198",
            "name": "Harry's car",
            "groupId": 32
        }'

-   for multiple devices at once - with the
    **POST /organizations/{orgId}/bulk-devices** call

        curl --request POST https://api-prod.surfsight.net/v2/organizations/{orgId}/bulk-devices
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
credentials, see [Tokens & credentials](tokens-and-credentials.md).

    curl --request POST https://api-prod.surfsight.net/v2/organizations/{orgId}/users
    --header 'Content-Type: application/json'
    --header 'Authorization: {token}'
    --data-raw '{

      "email": "email@email.com",
      "password": "123Abcd!",
      "role": "user"
    }'
