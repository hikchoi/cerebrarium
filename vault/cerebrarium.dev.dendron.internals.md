---
id: 59f0566b-24ea-4053-90e1-39a706a397e9
title: Internals
desc: ''
updated: 1614583583758
created: 1612791819408
---

# Dendron internals

> This is a compilation of notes about the internals of [Dendron](https://dendron.so/) that I keep while I work on the codebase. 

> This is **NOT** a comprehensive source of knowledge of them, just my little cheatsheet to complement my workflow.

# Topics

## windowWatcher
- listens to changes in the [window](https://code.visualstudio.com/api/references/vscode-api#window)
- currently (as of 2021-02-11), listens to change in active text editor, and update the text decorator that shows human readable timestamp of `updated` and and `created`

## DendronWorkspace
- 
