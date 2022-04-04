---
title: "Learning POSIX Shell"
date: 2022-04-03T18:45:10-07:00
draft: false
---

Being new to the Linux (and for that matter BSD, other POSIX OS) scene I had
never really gotten a chance to learn shell scripting. I've been using Linux
since summer 2020 and I've quickly understood the need for POSIX shell
scripting. 

When I first started out using Linux I excitedly "distro-hopped" in virtual
machines to try and find what flavor I liked best. As I result of this, I tried
a FreeBSD virtual machine and was surprised with how much software was
available. I also discovered that common utilies like `grep` and `sed` didn't
have all the features of their GNU counterparts. From then on I knew I had to
work on learning POSIX shell and to shun any bashisms. 

## Finding a project to work on

To start on this quest I needed a project to work on. I have been wanting to
improve my Spanish via passive listening. Passive listening is when you condense
the audio of videos you have already watched by cutting out the non-speaking
parts. This allows you to listen to this audio again during your daily commute
or on a walk while maximizing its learning potential. 

There have been various projects that condense audio of videos based on their
subtitle files. One of them [substudy](https://github.com/emk/subtitles-rs/blob/master/substudy/README.md) 
had a bug in it that prevented the majority of YouTube subtitle files from
working. Naturally as the FOSS advocate that I am, I sent in a pull request to
fix this. Sadly, it seems like the project is unmaintained. However, this
provided me with the perfect learning opportunity. 

## Learning POSIX shell

I set out to study what was allowed via the POSIX shell script standard.
[shellhaters](https://shellhaters.org) provides a convient way to reference this
standard. One of the vital lessons I learned is that the common shell utilies
that are provided are part of the standard and as such any call to them requires
special attention. For my particular project I learned early on that
`[[::digit::]]` would be required to parse time stamps in `sed`. Additionally,
`[[::digit:]]` would have to be repeated multiple times to accurately parse
timestamps. 

For example see this painful snippet:

```sh
# Delete blank lines after srt header
sed '/^[[:digit:]][[:digit:]]:[[:digit:]][[:digit:]]:[[:digit:]][[:digit:]],[[:digit:]][[:digit:]][[:digit:]][[:space:]]-->[[:space:]][[:digit:]][[:digit:]]:[[:digit:]][[:digit:]]:[[:digit:]][[:digit:]],[[:digit:]][[:digit:]][[:digit:]]/ {n;/^$/d;}' $PACIFILE-temp.srt > $PACIFILE.srt	
rm ./$PACIFILE-temp.srt
```

This took many hours and much
[duckduckgoing](https://duckduckgo.com) of "How to do x in POSIX shell?" or
"POSIX compliant version of x" and pulling up the relevant StackOverflow
results.

Other issues that I ran into were subtitle files having `\r\n` line endings
requiring a dependence on `dos2unix` which luckily can be found in both FreeBSD
and OpenBSD's repositories. Additionally, this project depends on the Python
utility `youtube-dl` as well as the venerable `ffmpeg`. After dealing with
temporary files and nested while loops, I can safely say that this project
should have been written in Python. I even already depend on Python due to the
dependency on `youtube-dl`!

```sh
# Combine adjacent timings and convert to mp3
p="00:00:00"
q="00:00:00"
while IFS=' ' read -r f s t
do 
  echo "$s:$t:$p:$q" > temp.txt	
  while IFS=':' read -r a b c x y z i j k l m n
  do	
...
```
> When you see this run!

As part of this project I was able to test that it was actually portable (not
all POSIX shell scripts are portable due to operating systems not being
completely compliant) by running it in Ubuntu 20.04, Alpine 3.13.5, FreeBSD
12.2, and OpenBSD 6.8 Virtual Machines.

## Conclusions

I would 100% recommend learning POSIX shell as it has helped me throughout my
many scripts I have made since then. I would also like to point out that POSIX
shell is not perfect for everything as was the case with this project. If it
gets out of hand like this one did, I would recommend transitioning to another
language that is very portable (Python usually fits this use case if you don't
need the performance). Please check out my Passive Listening script
[pacify](https://github.com/sirfredrick/pacify) which I may be porting to Python
in the future. Additionally, I have a virtual machine frontend script that
turned out to be a better fit for POSIX shell
[vm](https://github.com/sirfredrick/vm) let me know what you think. Please also
refer to [shellhaters](https://shellhaters.org) for any POSIX shell related
questions and get scripting!
