# A better and prettier mysql/mariadb CLI client

The default, unconfigured CLI client you use with mysql or mariadb is kind of
awful, no colors, pretty bad query editing capabilities, and the output is not
paged so you can't see a shit. Lets improve the experience.

![shot](shot.png)


## Client

Start by creating a configuration file `~/.my.cnf` with the following content:


    [client]

    user = alx
    password

Automatically prompt a password for your user, avoid giving `--user` option each
time

    no-beep

Stop making annoying noises god dammit!

    sigint-ignore

Is easy to type `^C` by accident, don't kill the session!

    auto-vertical-output

If the output is wider than the screen the output will look like shit, this fix
it

    i-am-a-dummy

Because, indeed, I am a dummy

    auto-rehash

You want completion, don't you?


### Prompt & color

    pager = "ccze -A | less -RSFXin"

Ok this is nice!, it will page your output using **less** only if the output
won't fit your screen. Also colorize it using **ccze** (which can make it a
little slower in some situations, so beware)

    prompt="\n[\d]   (╯°□°）╯- ┻━┻    "

Show me the current database and use the drop table donger as the prompt
(╯°□°）╯- ┻━┻  .... Drop table... Get it :D ?


You might want to configure **ccze** as well with the `~/.ccze` file:

    numbers green
    size yellow


## Input

The cli client uses
[readline](https://cnswww.cns.cwru.edu/php/chet/readline/rltop.html) so lets
configure it to get vi like bindings by creating a `~/.inputrc` file with the
content:

    $if mysql
        set editing-mode vi
    $endif

Pretty straight forward, just use vi editing mode for *mysql*


You can get all the configure files from my
[dotfiles](https://github.com/alx741/dotfiles):

https://github.com/alx741/dotfiles/blob/master/mysql/.my.cnf
https://github.com/alx741/dotfiles/blob/master/mysql/.inputrc
https://github.com/alx741/dotfiles/blob/master/ccze/.cczerc
