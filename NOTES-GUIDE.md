# How I take notes

Personal rules for this repo. The goal is notes I can review in 10 minutes, not a copy of the course.

## Structure

```
cyber-notes/
├── README.md              # index: what's here + progress
├── NOTES-GUIDE.md         # this file
├── linux/                 # Linux Journey, How Linux Works, Bash
├── bandit/                # OverTheWire (concepts only, no passwords)
├── networking/            # Jeremy's IT Lab (CCNA)
├── tryhackme/             # Pre Security and later paths
├── github-foundations/    # DataCamp track + exam prep
└── homelab/               # what I did on my server and why
```

## Naming

- `NN-topic-in-kebab-case.md` → `networking/01-network-devices.md`
- One file per lesson/day. If a topic grows too big, split it (`05a-`, `05b-`).
- Labs go in the same file as the theory, under `## Lab`.
- Packet Tracer files: `networking/labs/day01-lab.pkt`.

## Golden rules

1. **Only what I didn't know.** If I knew it from university, skip it or write one line.
2. **My own words.** If I can't explain it without copying, I didn't understand it yet.
3. **Write after watching, not while.** Watch → pause → write from memory → check the video for gaps.
4. **No secrets, ever.** No passwords (Bandit included), private keys, tokens, real IPs of my home network or Tailscale. `.gitignore` already has `key*`; when in doubt, don't commit.
5. **Commit every session.** Even if it's 3 lines. Small commits = visible progress.

## Template

```markdown
# <Topic> — <Source> Day N

**Date:** YYYY-MM-DD · **Source:** <link to video/lesson>

## Key ideas
- 3–7 bullets max, in my own words.

## New to me
- Things I didn't know or that surprised me.

## Commands / config
​```
command or config snippet
​```
What it does, in one line.

## Lab
- What I built, what broke, how I fixed it.

## Questions
- [ ] Things I still don't get → ask in the right chat or look up.

## Connect to security
- One line: how could this be attacked or defended? (optional, but good habit)
```

## Commit messages

```
networking: day 1 network devices
linux: text-fu notes
bandit: levels 6-10 concepts
homelab: ssh hardening log
```

Format: `<folder>: <what I added>`. Lowercase, short.

## Weekly review (Sunday)

- Re-read the week's "New to me" sections.
- Close or move open questions.
- Update the progress table in `README.md`.
