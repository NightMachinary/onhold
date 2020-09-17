# 🔊 Play music while and after a long job completes 

`onhold` is a command-line utility that allows you to play music while a long job completes.

`ding` is command-line utility that will play a sound when a long job completes. 

Both utilities will take data that is piped into their standard inputs and pipe it to standard output. That is to say that data piped into `onhold` and `ding` will be piped right back out.

```bash
$ echo "Hello!" | onhold
Hello!
```

## `onhold`

You can either set the `$ONHOLD` environmental variable to the song you'd like to play, or supply the song with the `-s` flag.

```bash
$ export ONHOLD="~/Music/song.mp3"
$ pv /dev/zero | onhold > /dev/null
```

This allows you to set `$ONHOLD` in your `~/.bashrc`

You can also specify it with a flag.

```bash
$ pv /dev/zero | onhold -s song.mp3 > /dev/null
```

## `ding`

You can either set the `$DING` environmental variable to the song you'd like to play, or supply the song with the `-s` flag.

```bash
$ export DING="~/Music/sound.ogg"
$ pv /dev/zero | ding > /dev/null
```

This allows you to set `$DING` in your `~/.bashrc`

You can also specify it with a flag.

```bash
$ pv /dev/zero | ding -s sound.ogg > /dev/null
```

# License
See `LICENSE`. If you'd like to use this project with a different license, please get in touch.


# Credit
## Music

See [`CREDIT.md`](/CREDIT.md).
