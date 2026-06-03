# Wellbeing Mentor

A personal health and wellbeing mentor system built on top of [Claude Code](https://claude.ai/code). It functions as a persistent, context-aware mentor that tracks your health across 8 domains, remembers your history, and challenges your thinking — not just your habits.

## How it works

The system is a Claude Code skill (`/mentor`) backed by a set of specialist subagents. When you open a conversation and type `/mentor`, the mentor reads your `brain/` files, picks up where you left off, and either runs a check-in or follows whatever you bring to the conversation.

For topics that need depth (nutrition, training, sleep, etc.), the mentor silently delegates to a specialist subagent, distills the response, and brings it back as conversation.

A `reflection-analyst` subagent can be triggered to scan your journal and segments and write behavioral/thinking patterns to `brain/patterns.md`.

## Project structure

```
.claude/
  skills/mentor/SKILL.md       # Mentor orchestration logic
  agents/                      # 8 specialist subagents + reflection analyst

brain/
  profile.md                   # Who you are, constraints, tone preferences
  goals.md                     # Long-term goals, weekly commitments, why behind each
  patterns.md                  # Thinking and behavioral patterns (reflection-analyst writes here)
  segments/                    # Current state per domain
    nutrition.md
    fitness.md
    sleep-recovery.md
    mental-emotional.md
    social.md
    habits-behavior.md
    environment-lifestyle.md
    preventive-health.md
  journal/                     # Append-only daily entries (YYYY-MM-DD.md)

health-segments.md             # Reference: full breakdown of all 45 health segments
```

## The 8 segments

| Segment | Covers |
|---|---|
| Nutrition | Food, hydration, supplementation, gut health |
| Fitness | Cardio, strength, mobility, daily movement |
| Sleep & Recovery | Sleep quality, recovery, posture, ergonomics |
| Mental & Emotional | Stress, emotion, mindset, cognition, purpose |
| Social | Relationships, community, communication, boundaries |
| Habits & Behavior | Habit design, time, goals, digital wellbeing, substance use |
| Environment & Lifestyle | Light, air, living space, food environment, financial health |
| Preventive Health | Checkups, screenings, hormonal, breathwork |

## Getting started

1. Clone the repo into a local folder
2. Open it in Claude Code
3. Type `/mentor` — if `brain/profile.md` is empty, the mentor runs onboarding across 2-3 sessions to build your brain from scratch
4. After that, every `/mentor` conversation picks up from where you left off

The `brain/` files ship empty. Your data stays local.

## Requirements

- [Claude Code](https://claude.ai/code) (desktop app or CLI)
- An Anthropic account with access to Claude
