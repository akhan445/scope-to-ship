# Scope to Ship

Agent skills that take an idea from a rough thought to a working app, and then keep growing it round by round. They teach as you go and adapt to your level. Works in any harness that reads `SKILL.md` (Claude Code, Codex, Cursor, …).

Inspired by [Learn AI Basics](https://github.com/challengepost/learn-ai-basics) by Devpost (MIT). See [What's different](#whats-different).

**Worked example:** [four-seasons-of-canada](https://github.com/akhan445/four-seasons-of-canada) was built with these skills; its `specs/` folder holds every document they produced.

## The ideas behind it

The entire process revolves around miniminzing cognitive debt.
- **Spec-driven development.** Nothing is coded until the idea, the product and the technical plan are written down and approved. Every later step builds on those documents.
- **Flipped interaction.** The agent interviews you. You bring the ideas and make the decisions, and it asks, probes and organizes.
- **Learning first.** You say what you want to understand or get better at, and the skills work it into the build.
- **For any developer.** Beginners get guided help. Experienced developers can keep it brief, or write the code themselves with the agent as a mentor.

## Install

```
npx skills add akhan445/scope-to-ship --all -y
```

Or copy the folders in `skills/` into your project's `.claude/skills/` (or `~/.claude/skills/` for every project). You need **node** and **git**, and an empty folder for your project.

## The sequence

| Skill | What happens | Output |
|---|---|---|
| `1-start` | Meet the agent, check your workspace, share your idea, experience and what you want to learn | `specs/learner-profile.md` |
| `2-scope` | Find or sharpen the idea, find its kernel, and cut it to a small proof of concept | `specs/scope.md` |
| `3-prd` | Define the product: screens, behavior, look and feel, edge cases, what's in and out | `specs/prd.md` |
| `4-spec` | Agree on the technical plan: stack, pieces, data, file structure | `specs/spec.md` |
| `5-build` | Build in small verified, committed slices, review, then add more rounds | `specs/checklist.md`, your app, `specs/app-map.html` |
| `6-ship` | Decide what's next: keep building, publish, submit, or something else | depends on your choice |

Run each skill by name. A fresh conversation between skills is fine, because the `specs/` files carry the context.

## How it works

**Prototype first, then rounds.** The first pass is a small proof of concept that proves your idea's core. After that you can keep going for as many rounds as you like. Each round is a short cycle: say what you want next, approve a few small slices, then build and verify them. Round 2 works like Round 7, until the prototype has grown into the full project.

**You pick how much the AI does.**
- **Learn- Built with 3 modes:**
    - **default:** the agent writes the code, explains each step and shows you where it lives.
    - **junior-dev:** you write most of the code; the agent acts as a senior mentor with hints, task cards and code review.
    - **pair:** the agent writes the boilerplate and leaves the key logic to you.
- **Fast:** the agent builds with less explanation and pauses for your feedback at planned checkpoints.

You can change the mode any time, and it's remembered when you resume.

**A learning wrap-up.** After the first build, a short activity ties a real moment in your project to a practice you can reuse, and you get an `app-map.html` with pointers into the code.

**What happens next is your call.** At `6-ship` you can keep building, publish a public GitHub repository, prepare a hackathon submission (for example Devpost), or something else. Submission text is always yours: the agent never writes it.

**Privacy.** Setup keeps `specs/learner-profile.md` and local credential files out of commits. Before anything goes public, the skills check files and history for secrets and private context.

## Progress lives in the files

There is no separate progress file. The `specs/` folder is the state:

- Each plan (`scope.md`, `prd.md`, `spec.md`, `checklist.md`) has `status: draft | approved`. "Looks good" approves a plan.
- `checklist.md` tracks the build mode, the slices, and the rounds (`### Round N`) with `- [ ]` / `- [x]` boxes. The current round comes from the highest heading, so a new conversation can resume without asking.
- Each skill starts by reading these files and saying where you are.

## What's different

Compared with the original Learn AI Basics skills:

- **Generic, not hackathon-specific.** No required demo video, time box or Discord step. Devpost submission is one option at the end.
- **More ways to learn.** Learn mode gains junior-dev and pair styles, where you write the code yourself.
- **More ways to continue.** `6-ship` is a decision, not a finish line. After verifying the build, it asks what you want to do next:
  - **Keep building:** it jumps back into `5-build`, which works out the current round from the checklist, asks what you want to add, and plans and builds just those slices. You can repeat this for as many rounds as you like.
  - **Publish on GitHub:** repo checks, then an optional demo.
  - **Prepare a hackathon submission**, such as Devpost.
  - **Something else:** for example deploying it or sharing it with a few people.
  - **Wrap up:** stop here.
- **Iterate to a full project.** Rounds of plan-then-build take the prototype past a first version, with the round tracked in the checklist.

## Layout

```
skills/<name>/SKILL.md          the skill
skills/<name>/templates/        document templates the skill fills in
skills/<name>/references/       deeper material the skill reads on demand
```

## License

MIT. Original work © Devpost; modifications © Abdullah Khan. See [LICENSE](LICENSE).
