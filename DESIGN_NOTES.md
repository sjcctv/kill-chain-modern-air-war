# Quickstart

## 1. Load the Skill Prompt

Copy the full text from:

```text
prompts/kill_chain_skill_v3_4.md
```

Paste it into your LLM/chat interface.

Then say:

```text
Start a new game of Radar Trap v3.4 Balanced.
```

## 2. Read the tactical map

Example:

```text
     A B C D E F G H I J K L
  4  . . M . . . . ? . . . .
  5  . . B . . . . ? . ? . .
  6  . . . . D . . . ? ! . .
```

Common symbols:

```text
B = F-35
E = EA-18G
M = MQ-9
D = decoy
? = suspected enemy node
! = high-threat area
x = destroyed unit
X = destroyed / mission-killed high-value node
s = suppressed / damaged SAM
```

## 3. Choose a plan

Reply with:

```text
1
```

or:

```text
方案2
```

## 4. Custom plans

If you write a custom strategy, the AI must not execute immediately. It must convert your intent into **Plan 4** and ask for confirmation before rolling.

## 5. Official combat results

A result is official only when it has a full roll block:

```text
Turn Roll #3
Die: D10
Round Seed: 123456
Formula: v3.4 Roll Hash
Die Result: 8

Calculation Stack:
+ F35 Strike +3
+ ARM Rating +2
- Target Defense 3

Threshold = 8
Result: Hit
```

## 6. Snapshot

Every planning turn must end with:

```text
[GAME SNAPSHOT v3.4]
...
[/GAME SNAPSHOT]
```
