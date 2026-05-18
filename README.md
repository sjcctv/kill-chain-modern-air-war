# Kill Chain: Modern Air War

**Kill Chain: Modern Air War** is a chat-native tactical wargame framework for modern air warfare.

It is designed for play through an LLM/chat interface, where the AI acts as referee, red-team opponent, intelligence officer, battle recorder, dice engine, and tactical advisor. The player controls Blue forces through natural-language decisions.

The flagship scenario is **Radar Trap v3.4 Balanced**, a small SEAD/DEAD engagement focused on stealth aircraft, anti-radiation missiles, decoys, SAM discipline, electronic warfare, fog of war, and tactical risk tradeoffs.

---

## What makes this different?

Kill Chain combines:

- Natural-language player decisions
- ASCII tactical maps
- Turn-by-turn option previews
- Fog-of-war separation between player intelligence and referee truth
- Reproducible dice rolls
- Calculation stacks for every key combat result
- Snapshot-based game state
- Structured custom-plan confirmation before execution
- Modern air warfare concepts: stealth, SAMs, ARM, ELINT, jamming, decoys, passive detection, fighter pressure

Useful comparison:

```text
Traditional tactical simulator:
High fidelity, heavy interface, steep learning curve.

Open-ended LLM roleplay:
Flexible, but often inconsistent and hard to audit.

Kill Chain:
Chat-native, tactical, structured, reproducible, and easy to play.
```

---

## Repository structure

```text
kill-chain-modern-air-war/
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── ROADMAP.md
├── prompts/
│   └── kill_chain_skill_v3_4.md
├── docs/
│   ├── QUICKSTART.md
│   ├── RULES_SUMMARY.md
│   ├── DESIGN_NOTES.md
│   └── SNAPSHOT_SCHEMA.md
└── examples/
    └── sample_turn.md
```

---

## Quick start

1. Open your preferred LLM/chat tool.
2. Paste the full prompt from [`prompts/kill_chain_skill_v3_4.md`](prompts/kill_chain_skill_v3_4.md).
3. Say:

```text
Start a new game of Radar Trap v3.4 Balanced.
```

The AI should output:

- Game Seed
- Turn 1 Round Seed
- Current tactical map
- Three plan options
- A recommendation
- Full game Snapshot

Reply with:

```text
1
```

or:

```text
方案2
```

or a custom strategy such as:

```text
让诱饵压 J8，F-35 保持静默。如果 J7/J8 达到 Targeted，F35-2 发射 ARM。
```

---

## Current scenario

### Radar Trap v3.4 Balanced

Blue initial forces:

- F35-1: A5, ARM 2, AAM 4
- F35-2: A7, ARM 1, AAM 4
- EA-18G: A9, AAM 2
- MQ-9: A3
- Decoy-1: A6
- Decoy-2: A8

Red hidden forces:

- SearchRadar: I6
- LongRangeSAM: J7
- FakeSAM / DecoyEmitter: J8
- PassiveDetectionNode: H5
- HQ16 MediumSAM: I8
- SHORAD: J6
- J10C: east/rear pressure from Turn 3
- C2Node: K6

---

## Key mechanics

### Fog of war

```text
Red Intel Known To Player
Red True State for AI Referee
```

The Snapshot can contain both for development and replay. Normal player-facing narrative must only use player-known intelligence.

### Reproducible rolls

Every turn has a Round Seed. Each roll uses the v3.4 Roll Hash formula:

```text
Base = RoundSeed + TurnNumber * 10007 + RollIndex * 7919 + DieSides * 104729
Hash = (Base * Base + 31 * Base + 17 * RollIndex * RollIndex + 97 * TurnNumber) mod 1000003
DieResult = (Hash mod DieSides) + 1
```

### Official result rule

A combat result is official only if it includes:

```text
Turn Roll #
DieSides
Round Seed
Formula
Die Result
Calculation Stack
Threshold
Result
```

---

## Status

This is a prototype prompt-based game system. It is currently intended for LLM-assisted play, not as a standalone software application.

---

## License

MIT License. See [`LICENSE`](LICENSE).
