# Seven products delivered with AI agents: what works and what doesn't

[Deutsche Fassung](fallstudie.md) · As of 11 November 2026

Between late September and mid-November 2026 I took seven products from idea to a working version. AI agents (Claude Code) wrote the code. My role was that of a product owner and project manager: concept, specification, backlog, priorities, acceptance.

This text describes what held up and what didn't. The numbers come from the repositories; how they were counted is explained at the end.

## The projects in numbers

| Project | Period | Days with commits | Commits | Automated tests | Status |
| --- | --- | --- | --- | --- | --- |
| [DerKurator AI](https://github.com/seb-nsu/DerKuratorAI) | 28 Sep – 9 Nov | 15 | 165 | 1,048 | version 1.6.0, pilot pending |
| [Ideenportal](https://github.com/seb-nsu/Ideaportal) | 12 Oct – 1 Nov | 7 | 77 | 728 | four releases built, click test pending |
| [TimeLog](https://github.com/seb-nsu/Timelog) | 19 Oct – 10 Nov | 7 | 114 | 464 | built, device tests pending |
| [Bitschmiede](https://github.com/seb-nsu/Bitschmiede) | 29 Oct – 4 Nov | 5 | 201 | 739 | playable, playtest pending |
| [Digital-Helfer](https://github.com/seb-nsu/Digital-Helfer) | 31 Oct – 2 Nov | 3 | 20 | – | in use |
| [Cloud Price Information](https://github.com/seb-nsu/Cloud-Price-Information) | 6 Nov – 10 Nov | 4 | n/a | 88 | version 2.1.0 |
| [Couch Quest](https://github.com/seb-nsu/Max-against-the-world) | 6 Nov – 10 Nov | 3 | 74 | – | in progress |

That adds up to about 650 commits in six and a half weeks. Roughly nine out of ten carry the agent as author. Days with commits are not working days: concept, review and acceptance don't show up in that column.

## The approach

Every project followed the same order:

1. **Concept:** target group, value, scope, and what is deliberately left out.
2. **Specification:** requirements with an ID and acceptance criteria; for calculation logic, examples worked out by hand.
3. **Build in stages:** one brief to the agent per stage, one pull request, one acceptance.
4. **Outside review:** a second model checks the concept or the result without knowing the history.
5. **Follow-up:** every finding is assigned to a story, deliberately deferred, or kept as an open point.

## What worked

**A specification with IDs.** Bitschmiede has 14 specifications with 603 rules and 203 test cases, each with its own ID. The agent names the ID in the test, in the code and in the commit. At acceptance I could ask "where is PRD-R31 implemented?" and got a location, not an explanation. Where two specifications contradicted each other, a reconciliation table with 47 entries decided, once and visibly.

**Review as a separate step.** The third review of the Bitschmiede concept found 65 contradictions and calculation errors before a single line of code existed, among them a range whose midpoint would have revealed the true value to the player. For Ideenportal, two reviews produced 94 proposals. They led to 50 new or changed stories and a new positioning: AI-written analysis is market standard in 2026 and no longer a unique selling point. I would not have seen that from inside my own concept.

**Rules, not AI judgement.** In DerKurator the AI neither calculates nor decides. Numbers come from code, the verdict from a rule engine, and the language model understands the question and explains the result. That made the product testable: the evaluation over 119 cases shows 89% correct verdicts and, more importantly, not a single wrong GO. I could not have accepted a product whose core is a language model in the same way.

**The rule set first.** For TimeLog, the working-time calculation with 35 test cases existed before there was a server or an app. All clients use the same rule set. The twelve business decisions behind it, such as whether standby ends the working day, are documented together with the rejected options.

**Keeping open questions visible.** The rule for the agent was: if something is missing in the specification, make the smallest plausible assumption, mark it in the code and add it to a list. Bitschmiede has 169 such markers in the code and 353 entries in the list. That sounds like a lot, and it is. But each of them would otherwise have been a silent decision by the agent.

## What didn't work

**"Built" is not "accepted".** This is the most important finding. Four of the seven projects end at the same point: the code is there, the tests are green, and the step with real people is missing. In TimeLog, six of twelve rows of the status overview still need a test on real devices or with real accounts. Bitschmiede is waiting for a playtest with two people, Ideenportal for a click test with seven or eight. The agents made building many times faster and testing with people not at all. The bottleneck moved, and I kept building for too long without clearing it.

**Scope grows because building is cheap.** Ideenportal has a backlog of 146 stories in four releases. All four releases were built, as far as that is possible without paid services and users, within days of the concept. In a conventional project, a pilot would have followed release 1 and changed releases 2 to 4. Now there is a product with company sign-in, interfaces and impact measurement that no user has seen. Part of it probably misses the actual need, and I don't know which part.

**Numbers only users can settle.** Many balancing values in Bitschmiede are estimates. Automated simulation runs show whether the economy tips over. They don't show whether the game is fun. The same applies to deadlines and thresholds in Ideenportal and to the break logic in TimeLog.

**Documentation falls behind the code.** At this pace, descriptions go stale within days. Several README files quoted outdated numbers or an old status. One review of Ideenportal found places where an architecture decision and the code no longer matched.

**Cleaning up for publication.** The repositories were not built for outside eyes. Before publishing, personal details, real domains and demo data linked to real organisations had to be replaced. For three projects the commit history was lost in the process, which is exactly the evidence for the approach this text describes.

## What I will do differently next time

1. **After the first release, nothing more is built until five people have used it.** The test with users is a gate in the plan and no longer an item on the list of open tasks.
2. **Scope follows what I can accept.** How much can be built is no longer the measure. A release I cannot check through myself within a week is too large.
3. **The repository is meant to be public from day one.** No personal details and no real names in demo data, so the history survives.

The only one of the seven projects in use today is the smallest. I built Digital-Helfer for my parents in three days and reworked it based on their feedback: the Spotify guides moved from the iPhone to the PC, and the guide for the TV media library now matches their television. It has 20 commits, no automated tests and two users.

## How the numbers were counted

- **Commits and days with commits:** from the git history of the main branch, including merges. For DerKurator, Bitschmiede, Ideenportal and Digital-Helfer from the original history before publication, because the public repositories were set up anew. For Cloud Price Information the original history is no longer available.
- **Share of the agents:** author of the commits without merges, 518 of 564.
- **Automated tests:** test functions counted in the source on 11 November 2026. Parametrised tests count once, so a test run reports higher numbers.
- **Rules, test cases, open questions (Bitschmiede):** unique IDs in `docs/spec/`, entries in `docs/OFFENE-FRAGEN.md`, markers `ANNAHME:` in the source.
- **Review proposals (Ideenportal):** unique IDs in `docs/05-review-v3/`; stories from the file `einarbeitung.md`.
- **Verdicts (DerKurator):** `docs/evals/EVAL_REPORT.md`, run without a language model.
