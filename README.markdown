# mydata-notifications

"MyData Notifications" is a command-line tool to send Mac OS X User Notifications,
which are available in Mac OS X 10.8 and higher.  It is a fork of
https://github.com/julienXX/terminal-notifier.

We build our own "MyData Notifications" binary for
https://github.com/monash-merc/mydata instead of using the terminal-notifier
binary from https://github.com/julienXX/terminal-notifier/releases,
because that seems to be the only reliable way to ensure that we get the
correct application icon in the notification.


## Download

Prebuilt binaries will be available from the
[releases section](https://github.com/wettenhj/mydata-notifications/releases).

## Usage

```
$ ./"MyData Notifications".app/Contents/MacOS/"MyData Notifications" -[message|group|list] [VALUE|ID|ID] [options]
```

In order to use "MyData Notifications", you have to call the binary _inside_ the
application bundle.


#### Options

At a minimum, you have to specify either the `-message` , the `-remove`
or the `-list` option.

-------------------------------------------------------------------------------

`-message VALUE`  **[required]**

The message body of the notification.

Note that if this option is omitted and data is piped to the application, that
data will be used instead.

-------------------------------------------------------------------------------

`-title VALUE`

The title of the notification. This defaults to ‘MyData’.

-------------------------------------------------------------------------------

`-subtitle VALUE`

The subtitle of the notification.

-------------------------------------------------------------------------------

`-sound NAME`

The name of a sound to play when the notification appears. The names are listed
in Sound Preferences. Use 'default' for the default notification sound.

-------------------------------------------------------------------------------

`-group ID`

Specifies the ‘group’ a notification belongs to. For any ‘group’ only _one_
notification will ever be shown, replacing previously posted notifications.

A notification can be explicitely removed with the `-remove` option, describe
below.

Examples are:

* The sender’s name to scope the notifications by tool.
* The sender’s process ID to scope the notifications by a unique process.
* The current working directory to scope notifications by project.

-------------------------------------------------------------------------------

`-remove ID`  **[required]**

Removes a notification that was previously sent with the specified ‘group’ ID,
if one exists. If used with the special group "ALL", all message are removed.

-------------------------------------------------------------------------------

`-list ID` **[required]**

Lists details about the specified ‘group’ ID. If used with the special group
"ALL", details about all currently active  messages are displayed.

The output of this command is tab-separated, which makes it easy to parse.

-------------------------------------------------------------------------------

`-activate ID`

Specifies which application should be activated when the user clicks the
notification.

You can find the bundle identifier of an application in its `Info.plist` file
_inside_ the application bundle.

Examples are:

* `org.mytardis.MyData` to activate MyData.app
* `com.apple.Safari` to activate Safari.app

-------------------------------------------------------------------------------

`-sender ID`

Specifying this will make it appear as if the notification was send by that
application instead, including using its icon.

Using this option fakes the sender application, so that the notification system
will launch that application when the notification is clicked. Because of this
it is important to note that you cannot combine this with options like
`-execute`, `-open`, and `-activate` which depend on the sender of the
notification to be ‘MyData Notifications’ to perform its work.

For information on the `ID` see the `-activate` option.

-------------------------------------------------------------------------------

`-open URL`

Specifies a resource to be opened when the user clicks the notification. This
can be a web or file URL, or any custom URL scheme.

-------------------------------------------------------------------------------

`-execute COMMAND`

Specifies a shell command to run when the user clicks the notification.


## License

All the works are available under the MIT license. **Except** for
‘Terminal.icns’, which is a copy of Apple’s Terminal.app icon and as such is
copyright of Apple.

Copyright (C) 2012-2015 Eloy Durán <eloy.de.enige@gmail.com>, Julien Blanchard
<julien@sideburns.eu>

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
