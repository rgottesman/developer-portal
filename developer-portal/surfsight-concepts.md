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