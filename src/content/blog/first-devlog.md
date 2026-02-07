---
title: "Arcane Gambit: In the beninging"
description: "Introducing a chess-meets-card-battler roguelike and the core vision behind it."
date: 2026-02-07
---

We're building **Arcane Gambit**, a turn-based tactical game that merges chess strategy with deck-building card game mechanics — with a small roamable hub between battles.

## The Core Concept

The idea is simple: **play cards to summon chess pieces onto a grid battlefield**. Pieces keep their familiar movement rules (pawns advance, knights leap, rooks slide, etc.), but captures aren’t instant — everything has **HP** and **attack**, so fights play out over a few turns.

Combat is **adjacency-based**: when enemies are next to each other, they can attack. That turns “classic chess positioning” into a real resource puzzle: when do you commit, when do you hold energy, and when do you trade?

And because we can’t help ourselves, the board isn’t always perfectly clean: tiles can generate with **elevation** and **obstacles**, and we’re already testing terrain cards that can reshape the battlefield mid-match.

## What We've Built So Far

The prototype is already playable end-to-end: you enter a match, place pieces via cards, spend energy to act, and try to take the enemy King.

Right now we’ve got:

- **Turn-based match flow** (player vs AI) with king placement, card play, movement, and adjacent attacks
- **Per-turn energy (in-match)** (currently 3) used for **card plays and movement**
- **Creature cards** for classic pieces (Pawn/Knight/Bishop/Rook/Queen/King) using chess movement rules
- **Spell cards** (Magic Missile, Reinforce, Draw Two, Blink)
- **Terrain cards** (Rise/Sink today; hooks exist for fire/clearing obstacles)
- **A heuristic AI** that plays a card, then chooses a scored move, then chooses a scored attack
- **Summoning sickness** so new pieces can’t immediately act

### What a match looks like right now

If you want the current “rules as implemented” view:

- Matches generate a **5×5** board (small for now). Tiles can roll random **elevation** (risen/sunken) and **obstacles**.
- The first hand is **King-only**: you place yours first, then the AI places theirs.
- Creature placement is restricted to spawn zones: **your first two rows** vs the AI’s **last two rows**.
- After you successfully play a card (or hit **Skip Phase**), you can select a piece to **move** and/or **attack**.
- Movement costs energy, and pieces have different movement costs (pawns are cheap, kings are expensive).
- Attacks are **adjacent**. If a King dies, the match ends immediately.

One important “prototype reality” note: Kings currently have **very low HP** (set to 1 in deck initialization) so matches resolve fast while we iterate.

## The Three-Person Team

This is a collaborative project between three developers, each bringing specialized skills:
- **Alex: Core Systems**: Match flow & rules, AI behavior, deck management, game architecture
- **Amanda: UI/UX Developer**: Building screens, card presentation, visual feedback, HUD systems
- **Mike**: Modeling chess pieces, animations, visual effects, board aesthetics


## What's Next

We’re deep into the gameplay loop from start to win/loss. The foundation is solid, but there’s a lot to flesh out and wire together:

- **Wire rewards into the end-of-match flow** (we already have a currency + difficulty system scaffolded; it just needs to be connected)
- **Make the shop “real”**: inventory generation exists, but purchases still need currency deductions + actually adding cards/upgrades to your deck
- **More cards and deeper deckbuilding**: additional spells, terrain interactions, and upgrades
- **More enemies**: elites/bosses and more varied AI behaviors
- **Overworld pressure**: the day timer, fragment fees, and world transitions (light/dark) are in progress and will define the roguelike pacing

There’s more we want to do, but we’re deliberately keeping scope tight until the core loop feels great.

## Why This Game?

We love games that combine deep strategy with quick, iterative gameplay. Chess is timeless but can feel rigid. Deck-builders offer creativity and adaptation. By merging these genres, we're aiming for something that's:
- **Tactically deep** but approachable
- **Endlessly replayable** through roguelike structure
- **Satisfying** in both short bursts and longer sessions

This blog will chronicle our journey from prototype to polished game. We'll share technical insights, design decisions, stumbling blocks, and victories along the way.
