<p align="center">
<img src="https://user-images.githubusercontent.com/59781900/180666828-3c90f3bf-0079-427f-aed7-277565567174.png" alt="Oloko logo">
</p>

# Oloko Archive

[Oloko](https://panfu.fandom.com/wiki/Oloko) was a virtual world created by Goodbeans GmbH, the makers of [Panfu](https://panfu.fandom.com/wiki/Panfu).

This repository contains information about Oloko, as well as the (incomplete) Flash client, which was archived before its closure.

## Why we publish it

First of all, these files were publicly available and are solely under the copyright of Oloko and Goodbeans GmbH. We do not have any rights to them.

Oloko has a very low popularity, so there have been hardly any private servers for it. The founders were considerate of us when they found out about our existence (and even congratulated us), so we assume the same for Oloko.

If you decide to use these files for a private server, we recommend that you include a notice on the website that you are not the original Oloko and are not supported by it or its company.

With the publication we would like to help interested parties in starting a private server for Oloko.

## What you need to know

There is no open source project that offers an AMF gateway or game server of Oloko.

While we already had something in development, we will not share this publicly.

### Flash client

The files in the `flashclient` folder contain audios, SWF files and configurations from Oloko's client.

You can easily embed the client as follows:

```html
<object type="application/x-shockwave-flash" data="http://oloko.test/flashclient/Panfufriends.swf" width="910" height="690">
    <param name="scale" value="noscale">
    <param name="quality" value="best">
    <param name="salign" value="TL">
    <param name="menu" value="false">
    <param name="base" value="http://oloko.test/flashclient/">
    <param name="allowScriptAccess" value="always">
    <param name="wmode" value="transparent">
    <param name="flashvars" value="information_server=http://info.oloko.test/gateway/amf/&langId=DE&user=test&pw=1234&mode=live">
</object>
```

When developing the AMF gateway and game server you can use the source code of the client to get started (we recommend [JPEXS decompiler](https://github.com/jindrapetrik/jpexs-decompiler)).

### AMF Gateway

Oloko wanted to be more technically advanced than Panfu, which is why it used the newer AMF protocol AMF3.

For PHP developers we recommend [AmfPHP](https://github.com/silexlabs/amfphp-2.0), it already has support for AMF3 and is very easy to extend.

To debug the AMF Gateway responses we recommend you to use [Charles Web Debugging Proxy](https://www.charlesproxy.com).

### Game server

The game server used the same packet structure as Panfu. In the source code of the client you can even find packets from Panfu (e.g. Hot Boom).

It uses the TCP protocol, the packets have a `|` character as a separator and the `\0` character at the end. You must split the incoming data chunk with the latter character.
