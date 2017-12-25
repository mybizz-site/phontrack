Check the [README](https://gitlab.com/eneiluj/phonetrack-oc#phonetrack-owncloudnextcloud-application) for the moment.

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
```https://mynextcloud.host.com/apps/phonetrack/log/ulogger/48947ce5d37d947f38724fb8b20d43d/ac98bb9b15afc3d028d845b7fce4ab2c```
and the one for Bob : ```https://mynextcloud.host.com/apps/phonetrack/log/ulogger/48947ce5d37d947f38724fb8b20d43d/8691aa01a76bb2d8b0db2d80e9b1ec8d```.

Let's be clear, this URL will NOT WORK : ```https://mynextcloud.host.com/apps/phonetrack/log/ulogger/48947ce5d37d947f38724fb8b20d43d/Bob``` because the name "Bob" is reserved.

This way you don't make it impossible for Alice or Bob to log as any other name but at least you know Bob can't log as Alice and Alice can't log as Bob.