---
title: Ep 7 - SvelteKit bughunt safari
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