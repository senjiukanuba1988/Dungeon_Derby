# Dungeon Derby

It's a game for 4-12 players. The players get separated into two even teams, Red vs Blue. If the number of players is odd (e.g. 7), the remaining player becomes a **ghost** who harasses the leading team to keep things fair. The teams both get placed into a procedurally generated dungeon at floor 0. At the beginning both teams have no equipment, no gold. The players then have to explore the floor to find various things:
- keys to open doors
- special items for solving puzzles and doing special mechanics
- equipment for combat (weapons, armor, spells)
- the stairs that lead down to the next floor
- monsters to fight and loot gold and consumables from
- shops where they can spend gold on consumables (heal potions, other potions) that are mainly helpful in combat
The team that first makes it through all the levels and finishes level 10 wins. There are bosses at lvl 5 and lvl 10 that are supposed to be fought as a team.

## Procedurally generating the dungeon

This is probably the most error-prone part but I think I can figure it out. Basically I view it this way.
We have a set of possible rooms, each with an entrance declared ("this is where you are supposed to enter"). Each exit of the room is labelled with what it requires, which is either nothing or a key or a puzzle-solving-item. For example: The entrance is where you come from, exit 1 is easily reachable (maybe you have to fight monsters or evade traps or something but you do not need a special item) and exit 2 is a door behind 2 holes in the ground so you need the feather to get across it. So we always know which places are reachable and what is needed to reach them. We can also put items behind obstacles that you need special items to reach, like a key.
So the idea is that for each level we prepare requirements in advance. "Get Yellow Key" (keys exist in yellow, red, blue and green) -> "Get Jump Feather" -> "Get Blue Key" -> "Exit". Each thing requires the one before, meaning you need the yellow key to get the jump feather, you need the jump feather (and maybe also the yellow key) to get the blue key and you need the blue key (and maybe also the other things) to get to the exit. It can also branch a bit, so maybe you can get 2 different keys from the start and you only need one of them to get this floor's puzzle solving item but you need the other one and the puzzle solving item to reach the exit.
Also, only one player has the puzzle solving item, things have to be designed in a way that that player can then open the way for the others to follow him if that's what is needed or he just has to press a button that only he can reach and that allows the others to solve a puzzle or open a door or something.
On levels 5 and 10 the boss fight is basically the place to reach and defeating the boss reveals the stairs or a key to open the door to the room with the stairs or so.
The number of rooms per level should also be set, like let's say 12 rooms for the first floor, 30 rooms for the final floor. The available rooms at each stage of a floor should also be decided beforehand (what you can reach, not what you can exit), in my earlier example that could be 4 rooms before the yellow key, 3 more (7 rooms) with yellow key, 2 more rooms (9) with jump feather and then the last 3 rooms (12 now) with the blue key.
Later floors can use rooms that require a puzzle-solving-item from the previous floors.

## Puzzles

There are puzzles that need a special item that allows you to interact with something in a way that you can't interact with before you have that item:
- Feather lets you jump over small holes
- bracelet lets you lift heavy things or push stone blocks
- torch lets you see in the dark and light things on fire
- grappling hook allows you to get across large gaps towards things it can attach to or to pick up items behind large gaps (too large to jump across)
- summon block spell lets you summon a block to stop water from flowing or get in the way of a laser or push a button down

Other puzzles involve flipping levers, pressing buttons, gathering special items for some device.. they do not have to happen in a single room but they should be color coded to match with what they trigger (yellow lever opens/closes yellow doors, that could be in another room).

## Monsters

We will need monsters of increasing difficulty as the players get better equipment with time. The first monsters should be slow, maybe not even targeted (just random movement) and weak but the further along the players get the monsters should become stronger, get abilities, there will be monsters with ranged attacks, etc and the bosses will require the players to work together, maybe one player has to get past the boss to do something behind the boss to make it vulnerable and then the others can attack it from the front, things like that.

## Items

### Item categories and progression

- **Equipment**: weapons (swords, spears, bows, etc.) can have bonuses like faster attack speed, more damage, or special effects. Armor, shields, and spell scrolls also get tiered. Rare variants of these items can add random bonuses such as "5% chance to block fire damage", "absorb 1 point of damage every 5 seconds", "regenerate 1 HP per 10 seconds" etc. Strength scales with floor; each successive level offers a higher tier.
- **Shield** – offhand item; 75 % chance to block ranged attacks and reduces incoming damage like armor.
- **Spell Charges** – Spells as offhand items have limited charges. When equipped they start at 0. They regenerate 1 charge per defined time (e.g., 10 s) up to a max (e.g., 2). A visual indicator shows the number of available charges and progress to the next. Regeneration only starts when at least one charge is missing.
- **Two‑handed Weapons** – when equipped, clear both mainhand and offhand, move previous items to inventory.
- **Inventory** – holds inactive items; can be passed or sold.
- **Roles** – no preset; all explore, puzzle solving is group dynamic, tank role emerges from equipment choices.
- **Consumables**: healing potions, buff potions, antidotes, etc. Used to sustain the team in combat.
- **Special Puzzle Items**: feather, bracelet, torch, grappling hook, summon‑block spell, mirror‑shard, grav‑bridge. Required to open doors or solve puzzles.
- **Keys & Tokens**: color‑coded keys, keyrings, unique lockpicks. Unlock doors and hidden rooms.
- **Treasure & Currency**: gold, gems, unique relics. Gold fuels the trader and shops.
- **Progression**: Each floor increases item rarity; some rare items are only dropable after boss defeats.
- **Item Variants / Tiers** – Items come in Tier 1 to Tier 10. Higher tier usually better, but sometimes a lower tier is more useful due to specific bonuses or lower charge limits. Common upgrades (e.g., +10% charge regen) are Tier 3+, rare upgrades (e.g., extra charge) are Tier 8+. Visual tier indicator helps players identify.
- **Drop Fairness** – The entire dungeon is generated at the start. Loot for each monster and chest is pre‑determined and the same for both teams, so no luck advantage.


## Odd Player Ghost

- If the total player count is odd (e.g. 7 players → 3 vs 3 + 1 ghost), the remaining player becomes a **ghost** who harasses the leading team.
- **Lead detection** (what makes a team "in the lead"):
  1. Floor number — the team on a lower floor (higher floor number, deeper underground) is always in the lead.
  2. Same floor — the team that has the floor's puzzle-solving item is in the lead.
  3. Same puzzle status — whichever team has more keys for opening doors on the lowest floor they've reached.
  4. If everything is even, nobody is in the lead and the ghost can only observe (no harassment).
- The ghost can move freely: walk through walls, travel up and down floors without using stairs.
- The ghost has a key that teleports it to the identical location in the other team's dungeon.
- Ghost abilities (only when there is a leading team):
  - Cast a *Slow* spell: slows a target player to 50% speed for 5 s (30 s cooldown).
  - Close an **Open Door**: shuts a door that has been open for ≥20 s for 10 s.
  - Create a **Decoy Exit**: opens a fake door that leads to a trap room, forcing backtrack.
  - **Reduce Vision**: dims lights in the leading team's current room.
  - Trigger a minor trap: randomly triggers a trap (e.g. falling rock) on a tile the leading team is about to step on.
- **Scoring**:
  - The ghost earns points by successfully delaying the leading team.
  - Points are awarded for:
    - Making a player wait in front of a closed door.
    - Dealing damage to a player while they are affected by the "Slow" spell.
  - The ghost's performance is tracked via a high score to be compared with other ghost play sessions.
  - The ghost's score can be converted into a time advantage for the team that was harassed more (e.g., 10 seconds of waiting = 1 second advantage). This ensures harassment is a trade-off. (Trissie's idea)
  - When one team finishes, if the other team was harassed more, a ghost timer appears based on the point difference. If the trailing team finishes before the timer runs out, they win.


## Monster Scaling

- Use a fixed curve: each floor adds +10 % damage and +10 % HP to all monsters.
- Gap between floors increases: floor 1 monsters are base; floor 2 monsters are 50 % more powerful as players will likely have gear by then.

## Additional Ideas

- **Team‑Sync Puzzles** – Doors that only open if two players stand in the correct spots *simultaneously*, forcing coordination.
- **Dungeon Trader** – Appears occasionally (not more than once every two floors). He appears for both teams in the same location and offers the same set of items. He is available to both teams simultaneously, though they might encounter each other while shopping. His stock is one-shot (once an item is sold, it's gone from both traders). He stocks a limited set of combat gear with a power rating equivalent to 1-2 floors ahead of the current floor (higher-tier items are expensive so you can't buy many), and an unlimited supply of consumables. A single higher-tier weapon or armor piece helps but doesn't trivialize the game, since a group of three players wears 12 items.
- **Stealth Monsters** – Ghosts that become invisible for 10 s, then visible again for a few seconds. These appear only after floor 3.

## UI

- **Main Gameplay Screen**:
  - **Bottom of screen**: Dedicated area for health bars and currently equipped actionable items (mainhand, offhand, and active puzzle item).
  - **Actionable Items**: Display items alongside their respective keybinds.
  - **Consumables/Quick Slots**: A quick-access section for consumables (potions, bombs, etc.).
  - **Spell Info**: Display current spell charges and the progress/timer for the next charge generation.
  - **Ghost UI**: If playing as a ghost, the health bar is replaced by a **Chaos Meter** to track score. The ghost sees small icons above/below players who hold a key or the floor's puzzle item to help identify "relevant" targets.
  - **Mini-map**:
    - A 5x5 grid showing the current room in the center and up to two rooms in each direction.
    - Teammates are marked as colored dots within their respective rooms.
    - Teammates outside the mini-map range are indicated by arrows pointing toward their direction.
    - Teammates on different floors are not displayed.
