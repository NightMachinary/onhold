# 🔊 Play music while and after jobs complete

`onhold` is a command-line utility that allows you to play music while a long job completes.

`ding` is command-line utility that will play a sound after a long job completes. 

Both utilities will take data that is piped into their standard inputs and pipe it to standard output. That is to say that data piped into `onhold` and `ding` will be piped right back out.

```bash
$ echo "Hello!" | onhold
Hello!
```

This means you can build pipelines with `onhold` and `ding`.

For example, you can download an ISO with `http`, visualize the progress with `pv`, play music with `onhold` while writing to `/dev/sdb1`, and when it's finished, play a sound with `ding`.

```bash
$ export URL="https://releases.ubuntu.com/20.04.1/ubuntu-20.04.1-desktop-amd64.iso"
$ http "$URL" | pv | onhold | ding > /dev/sdb1
```

## `onhold`

You can either set the `$ONHOLD` environmental variable to the song you'd like to play, or supply the song with the `-s` flag.

```bash
$ export ONHOLD="~/Music/song.mp3"
$ pv /dev/zero | onhold > /dev/null
```

This allows you to set `$ONHOLD` in your `~/.bashrc`.

You can also specify it with a flag.

```bash
$ pv /dev/zero | onhold -s song.mp3 > /dev/null
```

`onhold` comes with a default song that will play if neither `$ONHOLD` or `-s` are set, and it will print a warning to standard error so that standard ouput is unchanged.

```bash
$ echo "Hello!" | onhold
Please set $ONHOLD or use the -s flag.
Hello!
```

## `ding`

You can either set the `$DING` environmental variable to the sound you'd like to play, or supply the sound with the `-s` flag.

```bash
$ export DING="~/Music/ding.ogg"
$ echo "Hello!" | ding
Hello!
```

This allows you to set `$DING` in your `~/.bashrc`.

You can also specify it with a flag.

```bash
$ echo "Hello!" | ding -s ding.ogg
Hello!
```

`ding` comes with a default sound that will play if neither `$DING` or `-s` are set, and it will print a warning to standard error so that standard ouput is unchanged.

```bash
$ echo "Hello!" | ding
Please set $DING or use the -s flag.
Hello!
```

# Installation

## PyPI
```bash
$ python3 -m pip install onhold
```

## GitHub
```bash
$ python3 -m pip install -r requirements.txt
$ python3 setup.py install
```

# License
See `LICENSE`. If you'd like to use this project with a different license, please get in touch.


# Credit
## Music

See [`CREDIT.md`](/CREDIT.md).
