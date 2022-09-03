---
title: Ep 7 - SvelteKit bug hunt safari
date: '2022-09-03'
updated: '2022-09-03'
excerpt: This session we'll try to hunt down a perplexing bug Tony has found with SvelteKit when statically generating markdown files.
categories: 
- live-stream
---

## Agenda for this week
1. Weekly Journal Review
    - [Code Journal](https://acidtone.github.io/code-journal/)
    - [Teaching Journal](https://acidtone.github.io/teaching-journal/)
2. Walk-through of last week
3. Walk-through of the differences between builds `.403` and `.420` of SvelteKit
4. Walk-through of the buggy behavior that needs to be solved.
5. Upgrade `.420` to the latest `.465`.
6. New bug found!
7. Break time: Which to do?
    1. Downgrade SK/Vite to fix `Cannot stringify a function` when exporting markdown render function to `+page.svelte` from `+page.server.js`, OR
    2. Build a reproduction repo for the original page refresh bug (and potential run into the stringify bug again). Same same.
8. Research:
    - How to lock SvelteKit to a build version
        - Stackoverflow: [How do I lock sveltekit down to a version?](https://stackoverflow.com/questions/71795449/how-do-i-lock-sveltekit-down-to-a-version)
    - Will using a Svelte store solve the stringify issue?
        - [Svelte.js 3 Stores & State Management Tutorial](https://www.koderhq.com/tutorial/svelte/store-state-management/)
    - [How to create a proper reproduction](https://youtu.be/dB_YjuAMH3o?t=1348)
        - When creating an Issue, use the Bug Report template
            >  Reproduction
            > A link to a repository, or a fork of https://node.new/sveltekit, that reproduces the issue. Reproductions must be short, self-contained and correct and must not contain files or code that aren't relevant to the issue — please do NOT just paste a link to your project. Explaining how to reproduce is generally not enough. It pushes the burden of creating a reproduction project onto a small set of volunteer maintainers and isn't scalable. If no reproduction is provided, the issue will be closed.
        - Example procedure:
            1. Name your repro with a distinctive name so it doesn't collide with other repros in the maintainers' system.
            2. Start fresh:
                ```
                $ npm init svelte
                ```
            3. Select Skeleton project
            4. Select default for all options (i.e. "No")
            5. Install dependencies with npm, NOT Yarn or pnpm. npm is the gold standard.
            6. Use minimal code and files to reproduce the Issue.
                - A "perfect" example of an Issue repro: [URI Encoding inconsistent between SSR and Browser routers](https://github.com/sveltejs/kit/issues/4629)
                
## Relevant repos
- King of Tokyo clone
    - [github repo](https://github.com/browsertherapy/king-of-tokyo-clone/)
    - [live demo](https://browsertherapy.github.io/king-of-tokyo-clone/)
- [Project Boards](https://github.com/orgs/browsertherapy/projects)
- Archive projects
    - [King of Calgary](https://github.com/acidtone/king-of-calgary) ([Live Demo](https://acidtone.github.io/king-of-calgary/))
    - [Vanilla Dice Tower](https://github.com/acidtone/dice-roller-vanilla/) ([Live Demo](https://acidtone.github.io/dice-tower-vanilla))
    - [Vanilla Dice Roller WIP](https://github.com/acidtone/dice-roller-vanilla) ([Live Demo](https://acidtone.github.io/dice-roller-vanilla/))

## Cleanup
- Update schedule for next stream (README.md)