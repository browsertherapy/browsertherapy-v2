---
title: Ep 1 - Let's Build a Dice Roller
date: '2022-07-23'
updated: '2022-07-23'
excerpt: First episode! We'll be building a function that rolls traditional and custom dice.
---

## Agenda
1. What is Browser Therapy?
2. Introduction to King of Tokyo
3. Build Session: rolling a traditional die
4. Build Session: add support for a custom die
5. Build Session: creating SVG die faces

## What is Browser Therapy
### Goals
1. Have fun and escape!
    - First series will be building a board game.
2. Be accountable to yourself and code regularly.
    - Weekly episodes are scheduled so we stick with the process.
3. Master your craft.
    - How we code is more important than what we code.

### Some Coding Processes
- [Build sessions](https://gist.github.com/acidtone/271634bbc2c1b1b6b6ace82306480e2e)
- [Learning Journals](https://bigthink.com/the-present/learning-journals/) [breakdown](https://acidtone.github.io/teaching-journal/breakdowns/how-learning-journals-can-help-students-grow.html)
    - Tony's Learning Journals
        - [Coding Journal](https://acidtone.github.io/code-journal/)
        - [Teaching Journal](https://acidtone.github.io/teaching-journal/)
    - [A learning journal entry about learning journals](https://acidtone.github.io/teaching-journal/#jan-15-2022)

## Introduction to King of Tokyo
### Background resources
- [Directory of Board Game Mechanics](https://boardgamegeek.com/browse/boardgamemechanic)
    - Dice related mechanics in the list:
        - [dice rolling](https://boardgamegeek.com/boardgamemechanic/2072/dice-rolling)
        - [die icon resolution](https://boardgamegeek.com/boardgamemechanic/2856/die-icon-resolution)
        - [different dice movement](https://boardgamegeek.com/boardgamemechanic/2950/different-dice-movement)
        - [worker placement with dice workers](https://boardgamegeek.com/boardgamemechanic/2935/worker-placement-dice-workers)
- [White, Brown, and Pink: The Flavors of Tabletop Game Randomness](randomness-white-brown-pink-noise.md) by Geoff Engelstein

## Build sessions
### Source repos
- [King of Calgary Mockup](https://github.com/acidtone/king-of-calgary)
- [First attempt at a dice tower](https://github.com/acidtone/dice-tower-vanilla)
- [State diagram - first attempt](https://acidtone.github.io/code-journal/#june-3-2022)

## Session Notes
### Define the Problem and Goal
**Problem**: I can't roll a die!

**Solution**: Let's build a `roll()` that will role one die, either traditional (i.e. 1-6) or a custom die.
- All dice will be fair dice (isohedral)
- Focus on traditional game dice
    - 2, 4, 6, 8, 10, 12 and 20-sided dice only
- Dice can have either numbered or custom faces

### Plan it out: base dice roller functionality
One utility funtion
- one parameter
    - if integer `x`, roll an x-sided die by finding random integer between 1 and x
        - return integer
    - if array `y`, roll custom die by finding a random `index` between 0 and `y - 1`
        - return array item

### Brute force: base dice roller functionality
- [Initial commit](https://github.com/acidtone/dice-roller-vanilla/commit/02a21504f6e14a21521b4b29515f9b705273dd5f)
- [Walk-through](https://github.com/acidtone/dice-roller-vanilla/commit/6d4099701ef995bfb849ebfd6d88ee40d8782701)
- [Optimized](https://github.com/acidtone/dice-roller-vanilla/commit/8b15401cf7306fbc329e56ee3c268cab54f7308d)

### Session Goal: Build an interface for the dice roller
- Copy the functionality at the top of this page:
    - [King of Calgary](https://github.com/acidtone/king-of-calgary)

### Plan it out
- take the code from the above repo and centre it on the page

### Brute force
- [added roll interface](https://github.com/acidtone/dice-roller-vanilla/commit/133b6c4134aedac75f5bd436852881eac3a0e446)
- [Walk-through](https://github.com/acidtone/dice-roller-vanilla/commit/491d19c6d40ae151a805b0bfd573b35d6853d06b)

## Ideas for next week
- SVGs!!!
- Plan out a new interface???
- Build a proper Dice Tower!!!