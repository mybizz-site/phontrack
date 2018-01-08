# Logging methods

Does anyone know good and free ([as in "free speech"](https://www.gnu.org/philosophy/free-sw.en.html)) app which can log position to custom URL in background ? [Create an issue](https://gitlab.com/eneiluj/phonetrack-oc/issues/new?issue%5Bassignee_id%5D=&issue%5Bmilestone_id%5D=) if you do !

* With a web browser, on the session public logging page, check "Log my position in this session" (works better on Android than on IOS...)
* [OsmAnd gpx recording plugin](https://osmand.net/features?id=trip-recording-plugin#Online_tracking) (Android) is able to log to a custom URL with GET method. IOS version does not include recording plugin. Tested and approved.
* [GpsLogger](http://code.mendhak.com/gpslogger/#features) (Android) Very good ! The best IMHO.  Setup in : Options -> Logging details -> Log to custom URL . Able to bufferize positions (**\***).
* [Owntracks](http://owntracks.org/) (IOS/Android) Both version work. This app does not work without google services installed on Android. Quite funny to provide an app for those who want to keep control of their tracking information and force them to be tracked by google services...
* [µlogger](https://f-droid.org/packages/net.fabiszewski.ulogger/) (Android) Very light. Able to bufferize positions (**\***). To use µlogger, set the µlogger URL provided by phonetrack-oc as the "server URL" and put **any** value (they won't be used) as username / password.
* [Traccar](https://www.traccar.org/client/) (IOS/Android) Quite good, not very verbose. Able to bufferize positions (**\***).
* [OpenGTS](http://opengts.org/) which is more a standard than an app. I successfully used [GpsLogger](http://code.mendhak.com/gpslogger/#features) (OpenGTS mode) and [CelltrackGTS/Free](http://www.geotelematic.com/CelltracGTS/Free.html) (a few bugs with this one).

\* : When device looses connectivity, the app stores positions and sends everything when back online. 

# Device name reservation

## What is it ?

By default, there is no restriction and everyone who has the session's logging URL can choose whatever device name he wants. This means anyone can cheat on his identity. As the session's owner, if you want to prevent that, you can reserve some device names in PhoneTrack's user interface. To reserve a name means that only one person (that you choose) will be able to log with this name.

## How do i do it ?

To actually reserve a name : type the name in the reservation input field and type "ENTER". It will show you a "token" associated with the reserved name you just chose. Using this "token" as device name in a logging URL is now the ONLY way to log under the reserved name. This means anyone trying to use the reserved name directly in the logging URL will see his logging attempts refused.

## Example

I created a session to share positions with Alice and Bob. I want to make it impossible for Alice to log points with "Bob" a device name and Bob to log with "Alice" as device name.
Here is the Ulogger logging URL is : ```https://mynextcloud.host.com/apps/phonetrack/log/ulogger/48947ce5d37d947f38724fb8b20d43d/yourname```. Here are the reservation token i made for Alice and Bob :
```
Alice : ac98bb9b15afc3d028d845b7fce4ab2c
Bob : 8691aa01a76bb2d8b0db2d80e9b1ec8d
```

Here is the URL i can send to Alice for her to use it with Ulogger :
`https://mynextcloud.host.com/apps/phonetrack/log/ulogger/48947ce5d37d947f38724fb8b20d43d/ac98bb9b15afc3d028d845b7fce4ab2c`
and the one for Bob : `https://mynextcloud.host.com/apps/phonetrack/log/ulogger/48947ce5d37d947f38724fb8b20d43d/8691aa01a76bb2d8b0db2d80e9b1ec8d`.

Let's be clear, this URL will NOT WORK : `https://mynextcloud.host.com/apps/phonetrack/log/ulogger/48947ce5d37d947f38724fb8b20d43d/Bob` because the name "Bob" is reserved.

This way you don't make it impossible for Alice or Bob to log as any other name but at least you know Bob can't log as Alice and Alice can't log as Bob.