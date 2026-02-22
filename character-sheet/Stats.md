---
level: 3
hp-diced: 10
hp-current: 0
con: 14
con-mod: 2
hp-max: 27
hp-temp: 0
prof: 2
con-save: 2
str: 16
str-mod: 3
str-save: 3
athletics: 3
dex-mod: -1
dex: 8
dex-save-prof: 0
sleight-prof: 0
acrobatics-prof: 0
int-mod: 0
wis-mod: 3
chr-mod: 0
chr-save-prof: 1
int: 10
wis: 16
chr: 10
wis-save-prof: 1
religion-prof: 1
insight-prof: 1
medicine-prof: 1
chr-save: 2
deception: 0
intimidation: 0
performance: 0
survival: 3
survival-prof: 0
dex-save: -1
acrobatics: -1
sleight: -1
stealth: -1
int-save: 0
arcana: 0
history: 0
investigation: 0
nature: 0
religion: 5
wis-save: 5
passive-perception: 13
animal-handling: 3
insight: 5
medicine: 5
perception: 3
initiative: -1
spellcast-mod: 3
spell-save: 13
spell-attack: 5
animal-handling-prof: 0
persuasion: 2
persuasion-prof: 1
hp-cur: 27
dmg: 0
hp-mod: 0
---
Level: `INPUT[number:level]`
Proficiency: `INPUT[number:prof]`
Initiative: `VIEW[{dex-mod}][math:initiative]`

# HP
| Max                                                          | Temp                    | Current                |
| ------------------------------------------------------------ | ----------------------- | ---------------------- |
| `VIEW[8 + {level} * {con-mod} + {hp-diced} + {level}][math:hp-max]` | `INPUT[number:hp-temp]` | `VIEW[{hp-max} + {hp-temp} - {dmg}][math:hp-cur]` |

Damage: `INPUT[number:hp-mod]` `BUTTON[btn-dmg]`

```meta-bind-button
label: Damage
icon: ""
style: default
class: ""
cssStyle: ""
backgroundImage: ""
tooltip: ""
id: "btn-dmg"
hidden: true
actions:
  - type: updateMetadata
    bindTarget: dmg
    evaluate: true
    value: x + getMetadata("hp-mod")

```
# Constitution
Score:`INPUT[number:con]`
Mod: `VIEW[floor(number(({con} - 10) / 2), 0)][math:con-mod]`

| Name | Prof.                                             | Score                                         |
| ---- | ------------------------------------------------- | --------------------------------------------- |
| Save | `INPUT[toggle(offValue(0), onValue(1)):con-save-prof]` | `VIEW[{con-mod} + {prof} * {con-save-prof}][math:con-save]` |

# Strength
Score: `INPUT[number:str]`
Mod: `VIEW[floor(({str} - 10) / 2)][math:str-mod]`

| Name      | Prof.                                                   | Score                                                         |
| --------- | ------------------------------------------------------- | ------------------------------------------------------------- |
| Save      | `INPUT[toggle(offValue(0), onValue(1)):str-save-prof]`  | `VIEW[{str-mod} + {prof} * {str-save-prof}][math:str-save]`   |
| Athletics | `INPUT[toggle(offValue(0), onValue(1)):athletics-prof]` | `VIEW[{str-mod} + {prof} * {athletics-prof}][math:athletics]` |

# Dexterity
Score: `INPUT[number:dex]`
Mod: `VIEW[floor(({dex} - 10) / 2)][math:dex-mod]`

| Name            | Prof.                                                    | Score                                                           |
| --------------- | -------------------------------------------------------- | --------------------------------------------------------------- |
| Save            | `INPUT[toggle(offValue(0), onValue(1)):dex-save-prof]`   | `VIEW[{dex-mod} + {prof} * {dex-save-prof}][math:dex-save]`     |
| Acrobatics      | `INPUT[toggle(offValue(0), onValue(1)):acrobatics-prof]` | `VIEW[{dex-mod} + {prof} * {acrobatics-prof}][math:acrobatics]` |
| Sleight of Hand | `INPUT[toggle(offValue(0), onValue(1)):sleight-prof]`    | `VIEW[{dex-mod} + {prof} * {sleight-prof}][math:sleight]`       |
| Stealth         | `INPUT[toggle(offValue(0), onValue(1)):stealth-prof]`    | `VIEW[{dex-mod} + {prof} * {stealth-prof}][math:stealth]`       |

# Inteligence
Score:`INPUT[number:int]`
Mod: `VIEW[floor(number(({int} - 10) / 2), 0)][math:int-mod]`

| Name          | Prof.                                                       | Score                                                          |
| ------------- | ----------------------------------------------------------- | -------------------------------------------------------------- |
| Save          | `INPUT[toggle(offValue(0), onValue(1)):int-save-prof]`      | `VIEW[{int-mod} + {prof} * {int-save-prof}][math:int-save]`             |
| Arcana        | `INPUT[toggle(offValue(0), onValue(1)):arcana-prof]`        | `VIEW[{int-mod} + {prof} * {arcana-prof}][math:arcana]`               |
| History       | `INPUT[toggle(offValue(0), onValue(1)):history-prof]`       | `VIEW[{int-mod} + {prof} * {history-prof}][math:history]`              |
| Investigation | `INPUT[toggle(offValue(0), onValue(1)):investigation-prof]` | `VIEW[{int-mod} + {prof} * {investigation-prof}][math:investigation]`        |
| Nature        | `INPUT[toggle(offValue(0), onValue(1)):nature-prof]`        | `VIEW[{int-mod} + {prof} * {nature-prof}][math:nature]`               |
| Religion      | `INPUT[toggle(offValue(0), onValue(1)):religion-prof]`      | `VIEW[{int-mod} + {prof} * {religion-prof} + {wis-mod}][math:religion]` |

# Wisdom
Score:`INPUT[number:wis]`
Mod: `VIEW[floor(number(({wis} - 10) / 2), 0)][math:wis-mod]`

| Name | Prof.                                             | Score                                         |
| ---- | ------------------------------------------------- | --------------------------------------------- |
| Save | `INPUT[toggle(offValue(0), onValue(1)):wis-save-prof]` | `VIEW[{wis-mod} + {prof} * {wis-save-prof}][math:wis-save]` |
| Passive Perception |  | `VIEW[10 + {wis-mod}][math:passive-perception]` |
| Animal Handling | `INPUT[toggle(offValue(0), onValue(1)):animal-handling-prof]` | `VIEW[{wis-mod} + {prof} * {animal-handling-prof}][math:animal-handling]` |
| Insight | `INPUT[toggle(offValue(0), onValue(1)):insight-prof]` | `VIEW[{wis-mod} + {prof} * {insight-prof}][math:insight]` |
| Medicine | `INPUT[toggle(offValue(0), onValue(1)):medicine-prof]` | `VIEW[{wis-mod} + {prof} * {medicine-prof}][math:medicine]` |
| Perception | `INPUT[toggle(offValue(0), onValue(1)):perception-prof]` | `VIEW[{wis-mod} + {prof} * {perception-prof}][math:perception]` |
| Survival | `INPUT[toggle(offValue(0), onValue(1)):survival-prof]` | `VIEW[{wis-mod} + {prof} * {survival-prof}][math:survival]` |

# Charisma
Score:`INPUT[number:chr]`
Mod: `VIEW[floor(number(({chr} - 10) / 2), 0)][math:chr-mod]`

| Name | Prof.                                             | Score                                         |
| ---- | ------------------------------------------------- | --------------------------------------------- |
| Save | `INPUT[toggle(offValue(0), onValue(1)):chr-save-prof]` | `VIEW[{chr-mod} + {prof} * {chr-save-prof}][math:chr-save]` |
| Deception | `INPUT[toggle(offValue(0), onValue(1)):deception-prof]` | `VIEW[{chr-mod} + {prof} * {deception-prof}][math:deception]` |
| Intimidation | `INPUT[toggle(offValue(0), onValue(1)):intimidation-prof]` | `VIEW[{chr-mod} + {prof} * {intimidation-prof}][math:intimidation]` |
| Performance | `INPUT[toggle(offValue(0), onValue(1)):performance-prof]` | `VIEW[{chr-mod} + {prof} * {performance-prof}][math:performance]` |
| Persuasion | `INPUT[toggle(offValue(0), onValue(1)):persuasion-prof]` | `VIEW[{chr-mod} + {prof} * {persuasion-prof}][math:persuasion]` |
# Spellcasting
Spellcasting Modifier: `VIEW[{wis-mod}][math:spellcast-mod]`
Spell Save DC: `VIEW[8 + {spellcast-mod} + {prof}][math:spell-save]`
Spell Attack Bonus: `VIEW[{spellcast-mod} + {prof}][math:spell-attack]`
