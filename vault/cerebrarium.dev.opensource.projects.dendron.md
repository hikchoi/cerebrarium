---
id: 739ad898-dfbf-403f-8cc6-073cfcca103e
title: Dendron
desc: ''
updated: 1612007087706
created: 1609631769094
---

# Dendron

[Website](dendron.so)


## Useful links
[Your First Extension](https://code.visualstudio.com/api/get-started/your-first-extension)

## Commit conventions

- follow [conventional commits](https://www.conventionalcommits.org/en/v1.0.0/) with the following tags
- categories:
    - feat: feature - introduce new functionality
    - enhance: enhancement - improve existing functionality
    - fix: make something not broken
    - chore: backend improvements
    - spike: not complete commi

## Setup

- Do this every time you pull in from upstream
    - [build repo](https://dendron.so/notes/64f0e2d5-2c83-43df-9144-40f2c68935aa.html#3-build-repo)

## Notes

**2021-01-06**

- Grabbed my first issue a few days ago.
- Seems I need a bit of ts/js + VSCode extension development primer so I've been on that for the last few days
- First going through [the typescript handbook](https://www.typescriptlang.org/docs/handbook/) to get myself familiar with typescript.
- [Kevin](https://www.kevinslin.com/) has kindly offered help to get me started with contributing. The community is very welcoming to newcomers.

**2021-01-11**
- Scheduled a pairing sessions on 2021-01-13 7:30AM. 

[Writing Tests](https://dendron.so/notes/c84aa95c-83b9-4d52-90a1-eeec8f0ca84f.html)
- consider both single vault and multi-vault scenario.
    - `runLegacySingleWorkspaceTest`
    - `runLegacyMultiWorkspaceTest`
    - These set up mocks for single/multi vault testing.
        - example : [RenameNoteV2.test.ts](https://github.com/dendronhq/dendron/blob/master/packages/plugin-core/src/test/suite-integ/RenameNoteV2.test.ts#L131:L131)
    - [arguments](https://github.com/dendronhq/dendron/blob/master/packages/plugin-core/src/test/testUtilsV3.ts#L70:L70)
        - `ctx`
            - [vscode extension context](https://code.visualstudio.com/api/references/vscode-api#ExtensionContext)
            - collection of utilities private to an extension
        - `preSetupHook`
            - runs before init
        - `postSetupHook`
            - runs after init
        - `preActivateHook`
            - runs befor workspace activation
        - `postActivateHook`
            -
- [runJestHarnessV2](https://github.com/dendronhq/dendron/blob/58b3587f1e44f54635f77f7395f7b756f18e0c84/packages/common-test-utils/src/utils.ts#L119)
    - use shimmed jest methods to assert equality of actual and expected test outcome.

- engine test setup
    1. initialize engine
    2. seed it with fixtures for testing
    - may require testing in multiple environments (plugin, CLI, server, engine)
    - may require multiple test runners (jest / mocha)

**2021-01-14**

_Notes on pairing session_

Session goal
- Add a test for MarkdownPublishPod
- Show how tests are set up for Dendron

watch

```bash
cd bootstrap/scripts
./watch.sh
```
- Dendron is made up of a multiple typescript projects
- This script will watch all of them and compile them when you make change to the code.


Testing in Dendron
- All tests are managed with jest.
    - Except the plugin itself, which uses mocha
        - mocha is very well integrated into VSCode's [test harness](https://en.wikipedia.org/wiki/Test_harness)
- Any test code that are not testing plugin functionality are
    - located in the `__tests__` directory
    - in the file name formatted `TestName.spec.ts`
- To run a test, use VSCode tasks
    - `cmd` + `shift` + `p`, -> `Task: Run Task` in the command palette
    - Select the appropriate task to run.
        - These are vscode wrappers around bash scripts.
    - In our case, we want to test `MarkdownPod.spec.ts`
    - Type `npm:test:watch` in the task comman palette
    - There will be a number of selections, marked with which project's test it will be running.
        - Select the one marked with `pods-core`, as we are testing pods today.
    - This will open a terminal and run `jest --watch` on the specific test we are interested in.
        - Now jest will run all the tests for you every time you change your test code
- Writing new tests
    - Start a new [describe block](https://jestjs.io/docs/en/api#describename-fn), and give it an appropriate name.
    - Write a new test case.
        - Use `runEngineTest`
            - Multiple versions of this exists
            - Make sure you import the right version of this.
                - This is a typescript thing (?)
        - There are preset scenarios for testing
            - These are `PreSetupHookFunctions`
            - They set up hard-coded notes in a vault so that they can be used in a test
    - Quick jest tip: use snapshots to grab a test result (something long that you don't really want to construct manually), and use that for your assertions
        - These can be found in `__tests__/__snapshots__`
        - Don't forget to remove the snapshot code for the final test code if it isn't necessary.
    - Clean up any unused code / warnings
- After writing all the tests, check again by running the entire test suite
    - Run `Test: bootstrap` found under `Task: Run Task`
        - This will all tests in all packages.
        - We want to do this before commiting because Dendron is a mono-repo, and most packages have dependencies on each other.
        - We want to make sure our changes aren't breaking something elsewhere.
        - Github action that will automatically do this for every push will be coming soon.
- If you want to be more careful, you can also test the plugin itself at this point.
    - The above step tests every single package that is not a plugin.
    - To run tests for the plugin itself, run `Extension Integ Tests (plugin-core)`, which can be found in the Run pane.

**2021-01-20 9:19 PM**
- What is `MarkdownPublishPod` (and the new markdown parser) actually doing?
    - get note, given the file name.
    - get processor (?)
    - process given representation of a file(note.body) as configured on the processor
    
**2021-01-24 5:33 PM**
- Some test cases to think about for `MarkdownPublishPod`
    - empty note
    - note with links
        - wikilink
        - relative link
    - note with reference
        - note reference
        - block reference
        - block range reference
        - reference offset
        - wildcard header reference
        - wildcard child reference
        - wildcard complex reference (child, then header, then offset)
        - ~~recursive reference~~
    - ~~note with tags?~~
        - tags are just regular notes.
    - ~~note with katex?~~
        - not markdown

**2021-01-25 12:17 AM**
- pushed revised tests for `MarkdownPublishPod`
- not sure what the best way to structure tests would be
    1. bundle tests that are testing similar functionality into one test block
    2. have them all separate.

**2021-01-30 3:40 PM**
- decided to pick up [#410](https://github.com/dendronhq/dendron/issues/410)
- currently `selectionExtract` will delete the text selected text from the original location even if the file is not part of the vault. This is might not be desirable.
- As-is
    - delete extracted text from file regardless.
- To-be
    - check if the document we are extracting from is from the same vault.
        - If it is, delete extracted text.
        - otherwise, don't

**2021-01-30 8:41 PM**
- looks like nobody is working on this issue. will pick up.
- not sure if I should use `getByVaultPath` or `getVaultByNotePathV4`
    - `getByVaultPath` is marked @deprecated, but is still in use in one place
    - `getVaultByNotePathV4`
        - using this against a non-vault file will raise an exception.
        - is using a try/catch block for control flow something people do in js/ts?
