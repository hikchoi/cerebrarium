---
id: e8f4cfca-ac34-4751-8384-5e596ba07662
title: Timewarrior
desc: ''
updated: 1618846122037
created: 1618842713272
---

# Timewarrior

## Cheatsheet

start tracking
```sh
timew start
```

start tracking with tag "Dendron"
```sh
timew start Dendron
```

start tracking with more than two tags
- anything that looks like it needs escaping (or multi word) you just wrap it around quotes.
```sh
timew start Dendron "#470"
timew start Dendron "write tests for #470"
```

stop tracking
```sh
timew stop
```

cancel active time tracking
```sh
timew cancel
```

modify
- show the summary with ids
```sh
timew summary :week :ids
```

- then, select the @ interval you wish to modify
```sh
timew modify end @3 2021-07-13T00:00:00
```
