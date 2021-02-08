---
id: 7a2ab298-f46f-445c-9e6c-8f58d135ce7a
title: Actionables
desc: ''
updated: 1612604635012
created: 1608877391650
---

# Actionables

> A single place that lists immediately actionable tasks from various task.

## workflow
```
1. Add all actionable tasks into the inbox
2. Chop the tasks down to bite-size chunks
3. Move tasks into appropriate headings
4. Pick from the list of actionables what you should do today
5. Write that down in your physical daily note
6. Do it
7. At the end of the day (or when it is necessary), check what has been done
8. Every Sunday afternoon, go through the list and clean it up.
```

## notes
1. Keep this list as flat as possible. 
    - If a task needs a separate page for it, the scope of it is too large and probably doesn't belong here.
2. This list is not for every day chores or tasks that are necessary for basic survival.
    - Keep this in physical daily note
3. This list is not for work related tasks.
4. Ideally, life should be full of interesting stuff that this list never depletes.

## inbox

> Unsorted list of actionables waiting to be categorized, or does not fit into a bigger topic. 
Task that need more breaking down also belongs here until it becomes actionable.

- [ ] look into carbon steel woks
- [ ] repo for dotfiles?

## self(meta)
- [ ] sleep
- [ ] learning
- [ ] meditation
- [ ] ideals

## learning
- vim
    - [x] install vim plugin on vscode
    - [ ] figure out how to gradually introduce vim keybindings that I actually use
    - [ ] try following [Stephen's workflow](https://discord.com/channels/717965437182410783/717965437182410786/798338552761024552)

## open source

### dendron
- [x] work on issue [#417](https://github.com/dendronhq/dendron/issues/417)
    - [ ] ~~swap out old md parser~~ kevin did this for the pairing session
    - [x] add test case for `MarkdownPublishPod`
        - [x] learn how tests are set up
        - [x] write tests in `MarkdownPod.spec.ts`
            - [x] additional tests using other setup hooks
    - [x] cleanup
    - [x] read up on conventional commits
    - [x] commit
    - [x] push, PR
    - [ ] change requested [#458](https://github.com/dendronhq/dendron/pull/458)
        - [x] think about more test cases relevant to `MarkdownPublishPod`
        - [x] add `ENGINE_HOOKS` on some of those test cases
        - [x] add more tests
    - waiting for review.
- [ ] work on issue [#410](https://github.com/dendronhq/dendron/issues/410)
    - fix
        - [ ] check if extraction comes from known vault
        - [ ] don't delete selected text if it comes from a non-vault file
    - test
        - [ ] figure out mocha test setup
        - [ ] write tests
            - `LookupCommand.test.ts`
    - [ ] cleanup
    - [ ] commit
    - [ ] push, PR
- [x] pick up another `size.small`
- familiarize Dendron internals
    - [x] how to add `ENGINE_HOOKS` for mocking new test cases
    - [ ] figure out what procs are? [unifiedjs](https://unifiedjs.com/)
- familiarize VSCode internals
    - [ ] input boxes
    - [ ] quick picks
    - [ ] webview
    - [ ] vscode API primer
- [ ] feature request write-up for configurable root node

## [cerebrarium.garden](https://cerebrarium.garden)
- [ ] think about ways to do daily publishing
- [ ] look into 11ty theming
- [ ] hide certain hierarchies from navbar (e.g. notes)
- [ ] try to incorporate block references?
- [ ] fix old ref syntax to new one
- [ ] custom css for markdown preview
    - [ ] tweak css
        - [ ] codeblock styling
        - [ ] checkbox styling
        - [ ] anchor styling

## [markhyunikchoi.com](https://markhyunikchoi.com)
- housekeeping
    - [ ] merge separate post tag index components into one layout components
    - [ ] refactor image related components
        * glyphs
        * mdx image
        * logo
    - [ ] look into theme-ui
    - [ ] SEO optimization
    - [ ] add custom 404 page
    - [ ] clean up scattered layout components
- feature
    - [ ] bilingual pages
    - [ ] dark mode
- [ ] port to 11ty?
    - this is a lot of work. possibly a complete rework...

## modular synthesis
- [ ] plan focused sessions for learning currently owned modules
    - [ ] drum synthesis
        - [ ] kick drum
    - [ ] 0-coast
        - [ ] each section
- [ ] expand concept notes

## DIY
- [ ] learn how to order PCB from JLCPCB
    - [ ] FR4 panels
        - [ ] design with figma and inkscape (panel design plugin)
- [ ] research aluminum panels
    - [ ] purchasing sheets
    - [ ] drilling holes
        - [ ] drill bits
        - [ ] power drill
    - [ ] processing surface
- Teletype build
    - [x] order substitute socket for OLED screen
    - [x] order replacement U1
    - [ ] troubleshoot CV 3 output voltage.
    - [ ] find cheap keyboard
- Veils build (second)
    - [ ] sand down panel
    - [ ] build
- Kinks build
    - [ ] ~~R20, R21, R25, R32, R37~~
    - [x] source components
    - [ ] build
    - [ ] notes
- Fade build
    - [x] source components
    - [ ] compile IBOM
    - [ ] notes
- Tool notes
    - [ ] soldering iron
    - [ ] reflow plate
    - [ ] tweezers

## art
- [ ] reflection on art practice
- [ ] plan out Accidental Contraptions Q1 roadmap
- [ ] notes on model painting
    - [ ] Ma.K
- [ ] doodle stickers
    - [ ] research different sticker printing methods

## plants
- [ ] start logging plants.
    - [ ] lithops
        - how to kill them.
