[[_TOC_]]

# Logging methods

If you know a good and free ([as in "free speech"](https://www.gnu.org/philosophy/free-sw.en.html)) app which can log position to custom URL in background, [Create an issue](https://gitlab.com/eneiluj/phonetrack-oc/issues/new?issue%5Bassignee_id%5D=&issue%5Bmilestone_id%5D=) to let us know !

## Recommended

### [PhoneTrack-Android](https://gitlab.com/eneiluj/phonetrack-android)

(available on F-Droid)

Am i objective to judge this one ? It is different than all the other loggers because you can log to multiple destinations with different settings. Positions are stored if there is no network (**\***). It has a [very small impact on battery life](https://gitlab.com/eneiluj/phonetrack-oc/issues/175#note_130338568). To log with this app, create a new "PhoneTrack log job". If account settings are configured, just select a session and let the magic happen. Otherwise set the log job fields manually or import any PhoneTrack logging URL. Check the [PhoneTrack-Android user doc](https://gitlab.com/eneiluj/phonetrack-android/wikis/userdoc) for more details.

### [µlogger](https://f-droid.org/packages/net.fabiszewski.ulogger/)

(Android, available on F-Droid)

Very light. Able to bufferize positions (**\***). To use µlogger, set the corresponding logging URL provided by phonetrack-oc as the "server URL" and put **any** value (it won't be used) as username / password. This app is a Free Software, it's well designed, simple to use and focuses on logging.

### [GpsLogger](http://code.mendhak.com/gpslogger/#features) 

(Android)

Setup in : Options -> Logging details -> Log to custom URL . Able to bufferize positions (**\***).

### [OsmAnd gpx recording plugin](https://osmand.net/features?id=trip-recording-plugin#Online_tracking)

(Android)

is able to log to a custom URL with GET method. IOS version does not include recording plugin. Tested and approved.

## Other ones

### With a web browser

On the session public logging page, check "Log my position in this session" (works better on Android than on IOS...)

### [Owntracks](http://owntracks.org/)

(IOS/Android)

This app does not work without google services installed on Android. Quite ironic to provide an app for those who want to keep control of their tracking information but force them to be tracked by google services...

### [Traccar](https://www.traccar.org/client/)

(IOS/Android)

Quite good, not very verbose. Able to bufferize positions (**\***).

### [OpenGTS](http://opengts.org/)

which is more a standard than an app. I successfully used [GpsLogger](http://code.mendhak.com/gpslogger/#features) (in OpenGTS mode) and [CelltrackGTS/Free](http://www.geotelematic.com/CelltracGTS/Free.html) (a few bugs with this one).

### [LocusMap](https://www.locusmap.eu/)

which i never tried because it's proprietary and accessible just in amazon and google stores...

\* : When device looses connectivity, the app stores positions and sends everything when back online. 

# Logging apps comparison by @slaver

* Android 7.1 (stock samsung firmware):
    1. All apps don't work without Location services enabled.
    2. Only Traccar can operate with Location services via WiFi/Bluetooth/Network.

* Android 7.1 (LineageOS):
    1. All apps don't work without Location services enabled.
    2. All apps don't work with Location services via WiFi/Bluetooth/Network.
    3. Traccar v.5.8/5.7/5.6 doesn't work at all (even no GPS requests from that app).
    4. Traccar v.5.5 is OK.
    5. GPSlogger is a "champion" of battery usage, Traccar and uLogger eat far less.
    6. Traccar shows terrible track accuracy.
    7. GPSlogger has the best accuracy.
    ![screenshot](/uploads/8d8d8718e5913eae8d7c241122d0b795/screenshot.jpeg)

# Device name reservation

## What is it ?

By default, there is no restriction and everyone who has the session's logging URL can choose whatever device name he wants to log. This means anyone can cheat on his identity. As the session's owner, if you want to prevent that, you can reserve some device names in PhoneTrack's user interface. To reserve a name means that only one person (that you choose) will be able to log with this name.

## How do i do it ?

To actually reserve a name : type the name in the reservation input field and type "ENTER". It will show you a "token" associated with the reserved name you just chose. Using this "token" as device name in a logging URL is now the ONLY way to log under the reserved name with logging URLs. This means anyone trying to use the reserved name directly in the logging URL will see his logging attempts refused.

## Example

I created a session to share positions with Alice and Bob. I want to make it impossible for Alice to log points with "Bob" as device name and Bob to log with "Alice" as device name.
Here is the Ulogger logging URL is : ```https://mynextcloud.host.com/apps/phonetrack/log/ulogger/48947ce5d37d947f38724fb8b20d43d/yourname```. Here are the reservation token i made for Alice and Bob :
```
Alice : ac98bb9b15afc3d028d845b7fce4ab2c
Bob : 8691aa01a76bb2d8b0db2d80e9b1ec8d
```

Here is the URL i can send to Alice for her to use it with Ulogger :

`https://mynextcloud.host.com/apps/phonetrack/log/ulogger/48947ce5d37d947f38724fb8b20d43d/ac98bb9b15afc3d028d845b7fce4ab2c`

and the one for Bob :

`https://mynextcloud.host.com/apps/phonetrack/log/ulogger/48947ce5d37d947f38724fb8b20d43d/8691aa01a76bb2d8b0db2d80e9b1ec8d`.

Let's be clear, this URL will NOT WORK :

`https://mynextcloud.host.com/apps/phonetrack/log/ulogger/48947ce5d37d947f38724fb8b20d43d/Bob` 

because the name "Bob" is reserved.

This way you don't make it impossible for Alice or Bob to log as any other name but at least you know Bob can't log as Alice and Alice can't log as Bob.

# Geofences

A geofence is a square shaped zone defined for a device. When the device enters or leaves the geofence, an alert is sent.

When defining a geofence, you can set :

* the zone coordinates (duh)
* choose if an email should be sent
* choose the destination email address(es)
* the URL to visit when the device enter or leaves the zone
* if the URL should be queried with POST method or not (GET)

# Proximity alert

A proximity alert is defined with a pair of devices, a small and a big distance. The alert is triggered when the two devices get closer than the small distance or when they get farther than the big distance.

For both geofences and proximity alerts, user email is used if the email address field is left empty.

Emails will be sent only if Nextcloud's email settings are properly set.

# Sharing

There are multiple ways to share a session with PhoneTrack.

## Public session URL

Each session can be set public and then can be shared with a public URL. This URL allows the viewers to see all session points but everything is read-only.

## Public filtered share

You can create multiple public filtered shares for a session. First set and enable the filters, then create the public filtered share. The generated URL allows the viewers to see the session with those filters applied.

For each public filtered share, additional options are available :

### last positions only

If this is enabled, the public share will only show last devices positions.

### geofencify

If this is enabled, all points located inside a geofence will be showed at the geofence center. It is a kind of location simplification.

### Show one device only

You can restrict the public share to only display one device.

# Options

## Minimum distance to cut between two points

If this option is set to 1000m (for example), lines between two points which distance from each other is more than 1000m won't be displayed. The statistic table is also impacted.

## Minimum time to cut between two points

Same as previous option but with a duration. Those two options are not mutually exclusive, then can both be set at the same time.

# Point quota

Nextcloud admin can set a point number quota for PhoneTrack users. When a user reaches this amount of points, he/she can choose what happens :

* block logging : no new points can be logged
* delete user's oldest point each time a new one is logged : this will find the oldest point logged in any user's session and delete it each time a new point is logged. This way, the quota will never be exceeded.
* delete device's oldest point each time a new one is logged : each time a point is logged for a device, the oldest point of this device will be deleted before logging the new one. If this is the first point logged for this device, the oldest point of all existing device will be deleted.

# Session auto export

Users can choose to automatically export a session periodically. This action will be triggered by Nextcloud "cron tasks" at the requested frequency. Users can choose the path where automatic exports will be saved.

# Session auto purge

Automatic purge means periodical automatic point deletion for a session. For example, if weekly auto purge is set for a session, last complete week points will be deleted at the beginning of each new week.