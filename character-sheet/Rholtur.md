---
name: Rholtur
class: Kleriker
subclass: Forge Domain
deity: Feylara
race: Zwerg
level: 4
prof: 2
hp-diced: 14
hp-max: 34
hp-temp: 0
dmg: 0
hp-mod: 0
hp-cur: 34
exhaustion: 1
inspiration: false
hit-dice-used: 0
hit-dice-max: 4
death-save-success: 0
death-save-fail: 0
str: 16
str-mod: 3
dex: 8
dex-mod: -1
con: 14
con-mod: 2
int: 10
int-mod: 0
wis: 18
wis-mod: 4
chr: 10
chr-mod: 0
str-save-prof: 0
str-save: 3
dex-save-prof: 0
dex-save: -1
con-save-prof: 0
con-save: 2
int-save-prof: 0
int-save: 0
wis-save-prof: 1
wis-save: 6
chr-save-prof: 1
chr-save: 2
athletics-prof: 0
athletics: 3
acrobatics-prof: 0
acrobatics: -1
sleight-prof: 0
sleight: -1
stealth-prof: 0
stealth: -1
arcana-prof: 0
arcana: 0
history-prof: 0
history: 0
investigation-prof: 0
investigation: 0
nature-prof: 0
nature: 0
religion-prof: 1
religion: 2
animal-handling-prof: 0
animal-handling: 4
insight-prof: 1
insight: 6
medicine-prof: 1
medicine: 6
perception-prof: 0
perception: 4
survival-prof: 0
survival: 4
deception-prof: 0
deception: 0
intimidation-prof: 0
intimidation: 0
performance-prof: 0
performance: 0
persuasion-prof: 1
persuasion: 2
passive-perception: 14
initiative: -1
spellcast-mod: 3
spell-save: 14
spell-attack: 6
spell-slots-l1-used: 0
spell-slots-l1-max: 4
spell-slots-l2-used: 0
spell-slots-l2-max: 3
chain-mail: 17
shield: 2
shield-equipped: 1
hammer: 1
ac: 19
cp: 5
sp: 2
ep: 0
gp: 6
pp: 0
stone-cunning-used: 0
channel-divinity-used: 0
hammer-atk: 5
hammer-dmg: 3
_inspiring-leader: 6
---

> [!rholtur-hero]
> # 🔨 Rholtur
> **Kleriker (Forge Domain) – Level `INPUT[number:level]` – Diener der Feylara**
>
> | HP | Max | Temp | Erschöpfung | Inspiration |
> | :--- | :--- | :--- | :--- | :--- |
> | `VIEW[{hp-max} + {hp-temp} - {dmg}][math:hp-cur]` | `VIEW[8 + {level} * {con-mod} + {hp-diced} + {level}][math:hp-max]` | `INPUT[number:hp-temp]` | `INPUT[number:exhaustion]` | `INPUT[toggle:inspiration]` |
>
> Schaden / Heilung: `INPUT[number:hp-mod]` `BUTTON[btn-dmg]` `BUTTON[btn-heal]`
>
> | AC | Schild | Initiative | Pass. Wahrnehmung | Spell DC | Spell Atk |
> | :--- | :--- | :--- | :--- | :--- | :--- |
> | `VIEW[{chain-mail} + {shield-equipped} * {shield}][math:ac]` | `INPUT[toggle(offValue(0), onValue(1)):shield-equipped]` | `VIEW[floor(number(({dex} - 10) / 2), 0)][math:initiative]` | `VIEW[10 + {perception}][math:passive-perception]` | `VIEW[8 + {wis-mod} + {prof}][math:spell-save]` | `VIEW[{wis-mod} + {prof}][math:spell-attack]` |

```meta-bind-button
label: Schaden
icon: ""
style: primary
class: ""
cssStyle: ""
backgroundImage: ""
tooltip: ""
id: "btn-dmg"
hidden: false
actions:
  - type: updateMetadata
    bindTarget: dmg
    evaluate: true
    value: x + getMetadata("hp-mod")
  - type: updateMetadata
    bindTarget: hp-mod
    evaluate: false
    value: 0
```

```meta-bind-button
label: Heilung
icon: ""
style: primary
class: ""
cssStyle: ""
backgroundImage: ""
tooltip: ""
id: "btn-heal"
hidden: false
actions:
  - type: updateMetadata
    bindTarget: dmg
    evaluate: true
    value: x - getMetadata("hp-mod")
  - type: updateMetadata
    bindTarget: hp-mod
    evaluate: false
    value: 0
```

> [!rholtur-attr]- Attribute & Rettungswürfe
> | Attr | Wert | Mod | Prof | Save |
> | :--- | :--- | :--- | :--- | :--- |
> | **STR** | `INPUT[number:str]` | `VIEW[floor(number(({str} - 10) / 2), 0)][math:str-mod]` | `INPUT[toggle(offValue(0), onValue(1)):str-save-prof]` | `VIEW[{str-mod} + {prof} * {str-save-prof}][math:str-save]` |
> | **DEX** | `INPUT[number:dex]` | `VIEW[floor(number(({dex} - 10) / 2), 0)][math:dex-mod]` | `INPUT[toggle(offValue(0), onValue(1)):dex-save-prof]` | `VIEW[{dex-mod} + {prof} * {dex-save-prof}][math:dex-save]` |
> | **CON** | `INPUT[number:con]` | `VIEW[floor(number(({con} - 10) / 2), 0)][math:con-mod]` | `INPUT[toggle(offValue(0), onValue(1)):con-save-prof]` | `VIEW[{con-mod} + {prof} * {con-save-prof}][math:con-save]` |
> | **INT** | `INPUT[number:int]` | `VIEW[floor(number(({int} - 10) / 2), 0)][math:int-mod]` | `INPUT[toggle(offValue(0), onValue(1)):int-save-prof]` | `VIEW[{int-mod} + {prof} * {int-save-prof}][math:int-save]` |
> | **WIS** | `INPUT[number:wis]` | `VIEW[floor(number(({wis} - 10) / 2), 0)][math:wis-mod]` | `INPUT[toggle(offValue(0), onValue(1)):wis-save-prof]` | `VIEW[{wis-mod} + {prof} * {wis-save-prof}][math:wis-save]` |
> | **CHA** | `INPUT[number:chr]` | `VIEW[floor(number(({chr} - 10) / 2), 0)][math:chr-mod]` | `INPUT[toggle(offValue(0), onValue(1)):chr-save-prof]` | `VIEW[{chr-mod} + {prof} * {chr-save-prof}][math:chr-save]` |

> [!rholtur-skills]- Fertigkeiten
> | Fertigkeit | Prof | Bonus | Fertigkeit | Prof | Bonus |
> | :--- | :--- | :--- | :--- | :--- | :--- |
> | Athletics | `INPUT[toggle(offValue(0), onValue(1)):athletics-prof]` | `VIEW[{str-mod} + {prof} * {athletics-prof}][math:athletics]` | Deception | `INPUT[toggle(offValue(0), onValue(1)):deception-prof]` | `VIEW[{chr-mod} + {prof} * {deception-prof}][math:deception]` |
> | Acrobatics | `INPUT[toggle(offValue(0), onValue(1)):acrobatics-prof]` | `VIEW[{dex-mod} + {prof} * {acrobatics-prof}][math:acrobatics]` | Intimidation | `INPUT[toggle(offValue(0), onValue(1)):intimidation-prof]` | `VIEW[{chr-mod} + {prof} * {intimidation-prof}][math:intimidation]` |
> | Sleight of Hand | `INPUT[toggle(offValue(0), onValue(1)):sleight-prof]` | `VIEW[{dex-mod} + {prof} * {sleight-prof}][math:sleight]` | Performance | `INPUT[toggle(offValue(0), onValue(1)):performance-prof]` | `VIEW[{chr-mod} + {prof} * {performance-prof}][math:performance]` |
> | Stealth | `INPUT[toggle(offValue(0), onValue(1)):stealth-prof]` | `VIEW[{dex-mod} + {prof} * {stealth-prof}][math:stealth]` | Persuasion | `INPUT[toggle(offValue(0), onValue(1)):persuasion-prof]` | `VIEW[{chr-mod} + {prof} * {persuasion-prof}][math:persuasion]` |
> | Arcana | `INPUT[toggle(offValue(0), onValue(1)):arcana-prof]` | `VIEW[{int-mod} + {prof} * {arcana-prof}][math:arcana]` | Animal Handling | `INPUT[toggle(offValue(0), onValue(1)):animal-handling-prof]` | `VIEW[{wis-mod} + {prof} * {animal-handling-prof}][math:animal-handling]` |
> | History | `INPUT[toggle(offValue(0), onValue(1)):history-prof]` | `VIEW[{int-mod} + {prof} * {history-prof}][math:history]` | Insight | `INPUT[toggle(offValue(0), onValue(1)):insight-prof]` | `VIEW[{wis-mod} + {prof} * {insight-prof}][math:insight]` |
> | Investigation | `INPUT[toggle(offValue(0), onValue(1)):investigation-prof]` | `VIEW[{int-mod} + {prof} * {investigation-prof}][math:investigation]` | Medicine | `INPUT[toggle(offValue(0), onValue(1)):medicine-prof]` | `VIEW[{wis-mod} + {prof} * {medicine-prof}][math:medicine]` |
> | Nature | `INPUT[toggle(offValue(0), onValue(1)):nature-prof]` | `VIEW[{int-mod} + {prof} * {nature-prof}][math:nature]` | Perception | `INPUT[toggle(offValue(0), onValue(1)):perception-prof]` | `VIEW[{wis-mod} + {prof} * {perception-prof}][math:perception]` |
> | Religion | `INPUT[toggle(offValue(0), onValue(1)):religion-prof]` | `VIEW[{int-mod} + {prof} * {religion-prof}][math:religion]` | Survival | `INPUT[toggle(offValue(0), onValue(1)):survival-prof]` | `VIEW[{wis-mod} + {prof} * {survival-prof}][math:survival]` |

> [!rholtur-combat]- Kampf, Ausrüstung & Ressourcen
> ## Waffe
> **Smith's Hammer** (Spellcasting Focus)
> - Angriff: `VIEW[{str-mod} + {prof}][math:hammer-atk]`
> - Schaden: 1d6 + `VIEW[{str-mod}][math:hammer-dmg]` Bldg.
>
> ## Hit Dice & Death Saves
> | Hit Dice | Death Saves (Erfolg) | Death Saves (Misserfolg) |
> | :--- | :--- | :--- |
> | `INPUT[number:hit-dice-used]` / `VIEW[{level}][math:hit-dice-max]` | `INPUT[number:death-save-success]` / 3 | `INPUT[number:death-save-fail]` / 3 |
>
> ## Inventar
> - Kristallsplitter (ca. 7cm)
> - Anhänger von Veridania
>
> ## Münzen
> | Kupfer | Silber | Elektrum | Gold | Platin |
> | :--- | :--- | :--- | :--- | :--- |
> | `INPUT[number:cp]` | `INPUT[number:sp]` | `INPUT[number:ep]` | `INPUT[number:gp]` | `INPUT[number:pp]` |

> [!rholtur-spells]- Zaubersprüche
> ## Spell Slots
> | Level 1 | Level 2 |
> | :--- | :--- |
> | `INPUT[number:spell-slots-l1-used]` / `INPUT[number:spell-slots-l1-max]` | `INPUT[number:spell-slots-l2-used]` / `INPUT[number:spell-slots-l2-max]` |
>
> ## Cantrips (immer vorbereitet)
> ```dataview
> TABLE casting-time AS "Zeit", summary AS "Beschreibung"
> FROM "spells/level_0"
> WHERE prepared = true
> SORT file.name ASC
> ```
>
> ## Vorbereitete Sprüche (Level 1 & 2)
> ```dataview
> TABLE level AS "Lvl", casting-time AS "Zeit", summary AS "Beschreibung"
> FROM "spells/level_1" OR "spells/level_2"
> WHERE prepared = true
> SORT level ASC, file.name ASC
> ```

> [!rholtur-features]- Merkmale & Fähigkeiten
> ## Heroic Inspiration
> - [x] einen beliebigen Wurf wiederholen
> 
> ## Rasse (Zwerg)
> - **Darkvision** 60 ft
> - **Dwarven Resilience** Advantage auf Saves gegen Gift
> - **Stone Cunning** `INPUT[number:stone-cunning-used]` / 2 pro Long Rest
>
> ## Klasse (Kleriker)
> - **Channel Divinity** `INPUT[number:channel-divinity-used]` / 1 pro Short/Long Rest
>   - *Artisan's Blessing*
>   - *Turn Undead*
> - **Blessing of the Forge** 1/LR – +1 AC auf Rüstung (bereits in Chain Mail)
>
> ## Subklasse (Forge Domain)
> - Heavy Armor Proficiency
> - Smith's Tools Proficiency
> - Blessing of the Forge (s.o.)
>
> ## Besondere Ereignisse
> - Einmal gestorben und durch Diamant-Zauber wiederbelebt (Session 6)
> - Trägt den Anhänger von Veridania
