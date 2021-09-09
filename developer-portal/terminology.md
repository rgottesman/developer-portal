# Terminology

**auxiliary camera**

    A camera that can be installed on different spots of a vehicle to enable
    tracking of other perspectives during trips. Each auxiliary camera is
    associated with a single device.

**camera**

    A camera connected to the device, such as the road-facing camera, the
    in-cabin camera and auxiliary cameras.

**device**

    A video telematics device, such as the AI-12 dashcam.

**device configuration**

    You can configure your device settings. These settings include:

    - distractedDriver: enable or disable in-cabin audio and visual alerts when distracted driving events, such as cell phone usage, eating and drinking, or smoking, occur

    - textOverlay: enable or disable text overlay in video recordings and video events

    - inCabinCameraRecording: enable or disable in-cabin recordings. The distracted driver feature works whether or not the recordings are on

    - driverPosition: set the driver seat location - the left or right side of the vehicle. Must be set correctly for the distracted driver setting to work properly

    - speedUnits: set the units used for speed measurement to miles per hour or kilometers per hour

    - audioAlarms: enable or disable audio alarms from the device for dangerous and distracted driving events

    - notifyLiveStreaming: enable or disable on-screen text notifications when someone is viewing live video of the device

    - adminPIN: set the admin PIN

    - driverPIN: set the driver PIN

    - brightness: set the screen brightness to a value between 0 and 255.

    - dateTimeUnits: set the units used for date and time to \'us\' for US units or \'eu\' for metric units

    - voiceRecording: enable or disable recording audio in the vehicle

    - standby: set the time period after which the camera enters standby mode once the vehicle stops moving, between 1 and 60 minutes

    - hotspot: enable or disable internet access via the device hotspot

    - privacy: the privacy settings, which include:

        - gpsEnabled: enable or disable the GPS tracking

        - mvaiEnabled: enable or disable MVAI, machine vision and artificial intelligence, which identifies   distracted driving

        - cameras: enable or disable recordings and events for specific cameras

**event**

    Video of events from all cameras associated with a device (the 
    road-facing camera, the in-cabin camera, and any auxiliary cameras). The
    video is saved to the SD card and uploaded to the cloud. Events are any
    of a number of risky incidents that can occur during a trip, such as
    acceleration, violent turns, or distracted driving. Events can be
    configured to upload as text, snapshots, or videos. Video events capture
    5 seconds before and after the event occurs. The data tracked for each
    event includes the type of event, the date and time of the event, the
    location of the event, and the speed of the vehicle during the event.

**fleet**

     A number of vehicles, each with a device installed.

**group**

    Devices can be consolidated within a single group. Once you configure a
    group and associate any devices, you can then centrally manage those
    devices at the group level.

**IMEI**

    The unique identifier of the device.

    The IMEI number can be found on the sticker on the dashcam itself or on
    the back of the dashcam box.

**live stream**

    Live video from all cameras associated with a device (the road-facing
    camera, the in-cabin camera, and any auxiliary cameras). Live video can
    be streamed directly from the device, from the cloud, or through the
    API.

**organization**

    Individual devices and groups can be consolidated within a single
    organization. Once you configure an organization and associate any
    devices or groups, you can then centrally manage those devices and
    groups at the organization level.

**recording**

    Video of trips from all cameras associated with a device (the
    road-facing camera, the in-cabin camera, and any auxiliary cameras). The
    video is saved to the SD card and uploaded to the cloud.

**REST API**

    REST APIs allow for interaction with RESTful web services. In RESTful
    web services, requests made to a resource\'s URI receive a
    response formatted in HTML, XML, JSON, or some other format. REST APIs
    are defined in the [OpenAPIv3 definition
    file](https://swagger.io/specification/). 

**webhooks**

    Receive real-time event notifications from your devices to a URL of your
    choice.

**webRTC**

    Web real-time communication. This open source project helps to embed
    real-time voice, text and video in Web browsers without using plugins.
    This simplifies communication and improves user experience.