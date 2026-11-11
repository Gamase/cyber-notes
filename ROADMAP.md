# Cybersecurity Learning Plan

🌐 **English** · [Español](ROADMAP.es.md)

**Focus:** Blue Team / infrastructure security (a hypothesis to be confirmed in Phase 3).
**Pace:** ~6–7 hours per week, built to last, not to burn out.
**Started:** November 2026 · Back to the [dashboard](README.md)

---

## 1. Habit rules

1. **Same time, same place.** A fixed schedule (e.g., after dinner) that isn't renegotiated every day.
2. **Minimum viable: 20 minutes.** On a bad day (exams, fatigue), 20 minutes counts as a completed day: one Bandit level, one video, or a flashcard review.
3. **Never miss twice in a row.** Missing one day is normal. Missing two is how quitting starts.
4. **Mandatory rest.** Fridays and Sundays off. Rest is part of the plan.
5. **School comes first.** During exam weeks or residency deadlines, switch to "minimum mode" (20 minutes a day), guilt-free.
6. **Sessions with breaks.** 25–50 minute blocks with breaks in between. No all-nighters to "get ahead."
7. **Document everything** in this repo. It helps with review and doubles as a portfolio.

---

## 2. Typical week (~6.5 h)

| Day | Time | Focus |
|---|---|---|
| Monday | 60 min | **Linux**: theory (Linux Journey → later *How Linux Works*) |
| Tuesday | 60 min | **Networking**: 1–2 Jeremy's IT Lab videos + his Packet Tracer lab |
| Wednesday | 60 min | **Linux practice**: OverTheWire Bandit / Bash scripts |
| Thursday | 60 min | **Networking**: labs + Anki flashcards (Jeremy's IT Lab includes decks) |
| Friday | — | Rest |
| Saturday | 2 h | **Free practice**: TryHackMe + a home server project |
| Sunday | 15 min (optional) | **Weekly review**: what I learned, what's next, update notes |

10 minutes of Anki per day counts toward the session.

---

## 3. Phases (approximate timing at this pace)

### Phase 1 — Foundations (months 1–4)
- **Linux:** finish Linux Journey and Bandit (~30+ levels).
- **Networking:** first half of Jeremy's IT Lab (CCNA): OSI/TCP-IP, subnetting, switching, VLANs.
- **Security:** TryHackMe *Pre Security* (Saturdays).
- **Reading:** *Reflections on Trusting Trust* (Ken Thompson).
- **Home server:** harden it (key-only SSH, firewall, automatic updates, access log review).

**Goal:** comfortable in the terminal without looking up basic commands, and able to subnet by hand.

### Phase 2 — Programming + Advanced Networking (months 4–7)
- **Python:** *Automate the Boring Stuff* (Mondays and Wednesdays switch to Python).
- **Networking:** second half of the CCNA (routing, ACLs, NAT, security) + **Wireshark**.
- **Bash:** real scripts for the server (backups, alerts, log review).
- **Decide:** take the CCNA exam? Only with budget or a NetAcad discount.

**Goal:** a Python script that parses a log and flags something suspicious.

### Phase 3 — Security (months 7–10)
- **Security+ (SY0-801):** Professor Messer's course + practice. Use the **student discount**.
- **Track test (2 weeks):** one week of *SOC Level 1* and one of *Jr Penetration Tester* on TryHackMe.
- **Home server:** deploy **Wazuh** (SIEM) and monitor my own machines.
- **Bonus:** *Black Hat Python*.

**Goal:** Security+ exam taken and a track confirmed.

### Phase 4 — Specialization (month 10 onward)
- **If Blue Team:** finish SOC Level 1 → CySA+ or BTL1, detection engineering, and PowerShell.
- **If Red Team:** Jr Pentester → HTB Starting Point / Academy → PNPT or OSCP later on.
- **Both:** Go, AWS Cloud Practitioner (check AWS Educate vouchers), then cloud security.
- **Later:** *The Design and Implementation of the FreeBSD Operating System*.

---

## 4. First 4 weeks

| Week | Linux (Mon/Wed) | Networking (Tue/Thu) | Saturday |
|---|---|---|---|
| 1 | Linux Journey: *Grasshopper* · Bandit 0–5 | Jeremy's IT Lab days 1–3 (devices, OSI) · install Packet Tracer | TryHackMe account · Pre Security: intro |
| 2 | Linux Journey: *Command Line* · Bandit 6–10 | Days 4–6 (Ethernet, switching) | Pre Security: Network Fundamentals |
| 3 | Linux Journey: *Text-Fu*, *Permissions* · Bandit 11–14 | Days 7–9 (IPv4, intro to subnetting) | Pre Security: cont. · read *Trusting Trust* |
| 4 | Linux Journey: *Processes* · Bandit 15–18 | Days 10–12 (subnetting in depth) | Harden SSH on the server · monthly review |

**Monthly review** (last Sunday of each month, 30 minutes): Am I on pace? Am I enjoying it? Should I adjust anything? If I fall behind, the phase gets longer. Rest is never cut.
