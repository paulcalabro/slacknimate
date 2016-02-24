# slacknimate
> text animation for Slack messages :dancers:

EMOJI EXAMPLE HERE

## Installation
Download a binary from the Releases Page and put it somewhere on your `$PATH`.

_Mac users, want this installable via Homebrew? Please :star: this repo, as the
homebrew organization uses GitHub stars as the measure of popularity in deciding
whether to accept new recipes._

## Authentication
Simply grab your Slack user token from [this page][1].

You'll need to either pass it to the program via the `--api-token` flag or store
it as `SLACK_TOKEN` environment variable.

_If you want the message to come from a bot name/icon instead, see "Bots"
section at the bottom of this README._

[1]: https://api.slack.com/docs/oauth-test-tokens

## Usage

```
NAME:
   slacknimate - text animation for Slack messages

USAGE:
   slacknimate [options]

VERSION:
   1.0.0-alpha

COMMANDS:
   help, h	Shows a list of commands or help for one command

GLOBAL OPTIONS:
   --api-token, -a      API token* [$SLACK_TOKEN]
   --delay, -d "1"      minimum delay between frames
   --channel, -c        channel/destination* [$SLACK_CHANNEL]
   --loop, -l           loop content upon reaching end
   --preview            preview on terminal instead of posting
   --help, -h           show help
   --version, -v        print the version
```

### Simple animation loops

    $ slacknimate -c "#general" --loop < examples/emoji.txt

SCREENCAP**

### Realtime process monitoring
Why spam a chatroom with periodic monitoring messages when you can have realtime
status updates so that a message is never out of date?

See for example this example:

```
$ ./examples/process.sh 5 | slacknimate -c "#devops"
2016/02/23 19:03:14 initial frame G07AJU0SH/1456272194.000086: Processing items: 0/5
2016/02/23 19:03:15 updated frame G07AJU0SH/1456272194.000086: Processing items: 1/5
2016/02/23 19:03:16 updated frame G07AJU0SH/1456272194.000086: Processing items: 2/5
2016/02/23 19:03:17 updated frame G07AJU0SH/1456272194.000086: Processing items: 3/5
2016/02/23 19:03:18 updated frame G07AJU0SH/1456272194.000086: Processing items: 4/5
2016/02/23 19:03:19 updated frame G07AJU0SH/1456272194.000086: Processing items: 5/5

Done!
```

SCREENCAP**

### Preview in terminal
If you aren't certain about your source, you can preview what the animation
would look like in the terminal via the `--preview` flag.

    $ slacknimate --preview --loop -d 0.1 < examples/sample.txt


## Bots
In order for Slack message editing to work, the message _must_ be posted
`as_user: true`, which will show as coming from whomever owns the token. This
is due to how the security model for Slack message editing works.

For bots, you must create a new bot in the team settings and substitute in the
auth token for that bot.
