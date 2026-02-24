---
title: "Arcane Gambit: February 2026 update"
description: "Good chunks"
date: 2026-02-27
---

February brought the biggest expansion to Arcane Gambit since we started. 🎉 Last month we had a working game loop -- place pieces, spend energy, take the king. This month we have been building the world *around* that loop: a real economy, elemental combat, card upgrades, a hub you can actually walk around in, and the first hints of a story.

Here is where things stand.

## Elemental Combat

The biggest gameplay addition is a full elemental system. Cards now have an attack element -- Fire, Ice, Sand, or None -- and pieces carry individual resistances to each. A Pawn of Fire hits an Ice Pawn for bonus damage; an Archon Bishop is ice-aspected and resists its own element. Resistances compound, which means deckbuilding now involves real trade-offs: a tanky fire-resistant rook might melt to a frost nova.

On the spell side, the roster has grown considerably:

- **Fireball** -- AOE burst centered on a target tile
- **Ice Spear** -- line pierce that hits everything in a column from the target outward
- **Sandstorm** -- wide area suppression, desert biome-flavored
- **Frost Nova** -- AoE freeze burst for the winter board
- **Void Pulse** -- void biome crowd control

Magic Missile, Reinforce, Blink, and Draw Two are all still in, now sitting alongside the new spells. The spell system handles target modes per card type (single enemy, friendly piece, AOE pattern, line) so adding new spells is clean and isolated.

## The Forge and Card Upgrades

Between matches you can now upgrade your cards. The Forge lets you apply upgrades to individual cards from a weighted pool -- some universal (Tempered for +ATK, Hardened for +HP), others specific to a card type. A Knight can pick up Joust or become a Shadow Knight. A Bishop can ascend to an Archon with ice attacks. A Pawn can earn Promotion and become a Squire, or gain elemental aspecting entirely.

Each upgrade is tracked on the card itself -- display name can change, stats are modified directly, and the upgrade history is stored so the UI can show what a card has been through. Stackable upgrades like Tempered can be applied multiple times; named upgrades like Shadow Knight are one-time transformations.

This is the first system that makes the deck genuinely yours over a run.

## The Hub is Alive

The roamable hub between battles has graduated from a placeholder to a functioning space. The player character walks, looks around, and triggers interactions with objects in the world. Two distinct shops are in:

- **The Store** -- opens after 7pm in-world time, the player walks up and triggers a smooth camera transition into the shop view
- **The Special Store** -- a second vendor with different availability rules (still finalizing what makes this one distinct)

Camera transitions are shared infrastructure -- the same coroutine handles entering a match, entering a shop, and returning to roaming, so everything feels consistent.

## The Day System

The overworld has a real day cycle now. Each day runs on a 15-minute real-time clock from 7am to midnight. The day manager fires events that other systems subscribe to -- the HUD can update a clock, the shop can gate itself behind the hour, and the sleep interactable checks that it is actually evening before letting you rest.

Sleeping advances the day counter and triggers a fade-to-black transition. Fragments -- the short-term daily currency -- have to be paid each day via a separate interaction, and the cost scales exponentially with day number. Survive enough days and the run ends in victory. Run out of fragments or lose your king, and it does not.

The economy plumbing is real now: a centralized CurrencyManager handles dark and light energy (the persistent currencies) with event notifications for UI, and save data persists everything to disk as JSON -- current day, both currencies, fragment counts, difficulty counter, match history flags. If you close the game and reopen it, the run picks back up where it left off.

## Two Worlds

The light/dark world split is no longer just a concept. The GameManager carries a world flag that drives skybox selection, ambient intensity, and reflection settings. The board generator has separate roots for light and dark boards, and the save data tracks whether the player has crossed into the light world yet. The darker ambient settings for the dark world are already tuned; the light world gets a brighter, skybox-driven look.

Biome variety on the boards has expanded too. The obstacle system now supports six obstacle types -- tree, boulder, rock, cactus, ice wall, void crystal -- and each biome filters to its own subset at generation time. A desert board spawns cacti; a void board gets void crystals. The spell pool matches: Sandstorm and Frost Nova are board-thematic, not just generic AoE.

## A Story is Starting

There is a named boss in the save data now: Dark Jeff. That is not a placeholder -- he is the first scripted opponent and has his own AI subclass separate from the general heuristic. The AI architecture now separates scripted encounter logic from the generic evaluation code, which means we can write bespoke behavior for specific fights without touching the general-purpose AI.

The dialogue system is live too. The DialogueManager runs a typewriter display with punctuation-aware pacing -- pauses are longer after periods, shorter after commas. Dialogues are authored in a dialogues.json file under Resources and loaded at runtime, so Mike or Amanda can add or edit NPC lines without touching code. A full tutorial manager is also built and wired into match events -- it is sitting disabled right now while we focus on the core loop, but the infrastructure is there.

## Where We Actually Are

Everything above is in the codebase and functional, but functional and fully wired together are not the same thing. The tutorial is ready but off. The store UI exists but purchases still need to correctly deduct fragments and add cards to the deck. The Forge needs a proper UI pass from Amanda. The day counter and fragment fees run correctly, but there is no failure-state screen yet when you cannot pay.

We are aware of the gap between systems built and systems integrated. That is deliberately where our energy is going in March -- closing loops, wiring rewards, and making sure a full run from day one to the Dark Jeff encounter plays through cleanly.

## The Three-Person Reality

Alex has been heads-down on systems this month -- economy, elements, upgrades, dialogue infrastructure. Amanda is finishing the card upgrade UI and the store purchase flow. Mike is working on the piece models and biome-specific visual assets that will make the board feel like it belongs to a place.

We are getting close to a run that tells a complete story. More soon. 🔜

