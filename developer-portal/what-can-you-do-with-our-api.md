## What can you do with our API?

The Surfsight API enables you to manage devices and track events by
making calls using the following endpoints:

| Name         | Description             | Endpoints                   |
|-----------|----------|---------|
| Alarms | Receive alarms reports, manage report email recipients, and manage alarms. | /alarms |
| Audit logs | Receive your organization audit logs. | /audit-logs |
| Authentication | Authenticate yourself to access the Surfsight API | /authenticate |
| Device operations | Manage your device operations, such as formatting SD cards and receiving data usage.   | <ul><li>/devices/{imei}</li><li>/organizations/{orgId}/devices</li></ul> |
| Devices | Manage your devices and receive data about your devices, such as a device\'s settings or active cameras. | <ul><li>/devices/{imei}</li><li>/organizations/{orgId}</li></ul> |
| Events | Configure event settings and receive data about your events, such as event settings or an event\'s details. | /devices/{imei} |
| Geofences | Set geofences and receive a list of a device\'s geofences. | /devices/{imei}/geofences |
| Groups | Create and manage groups. | /organizations/{orgId}/groups |
| Health | Receive alarms reports and manage report email recipients. |  <ul><li>/device-health</li><li>/recipients/health</li></ul> |
| Organizations | Create and manage organizations. | /organizations |
| Partner operation statistics | Receive your operational statistics. Only partners can make these calls. | /partners/operational-statistics |
| Partners | Manage your partner contacts. | /partners/{pernterId} |
| Recordings | Receive data about recordings availability for a device\'s cameras and snapshots of a camera\'s current view. | /devices/{imei} |
| Streaming | Prepare live streaming from a device. | /devices/{imei}/connect-media |
| Telemetry | Receive telemetry data from a device or camera. | /devices/{imei} |
| Users | Manage users. | /organizations/{orgId}/users |
| Virtual events | Generate virtual events. | /devices/{imie}/virtual-event |
| Webhooks | Mange your webhooks subscriptions. | /organizations/{orgId}/webhooks |

These endpoints are detailed in the
[API reference]().
