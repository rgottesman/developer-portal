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