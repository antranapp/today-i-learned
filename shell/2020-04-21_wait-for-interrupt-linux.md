---
title: How to wait for Ctrl-C in bash
createdAt: 2020-04-21T23:10:44Z
---

# How to wait for Ctrl-C in bash:

- https://stackoverflow.com/questions/36991903/idle-bash-script-until-ctrlc-event-is-logged
- On Ubuntu, we need to use `INT` instead of `SIGINT`
- Working script: https://github.com/antranapp/FlutterTODOsTutorial/blob/master/screenrecord.sh