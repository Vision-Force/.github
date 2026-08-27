# Contributing to Vision Force

Thank you for taking the time. This page explains what is useful to send, and
what happens after you send it.

## Who you are talking to

Vision Force Studio is a fan team of community volunteers, having a studio as a
hobby project. One person, [@ShrezesUverse](https://github.com/ShrezesUverse),
reads and answers what arrives here. That has two honest consequences.

- Replies take time. Days is normal, longer when a build is in progress. Silence
  is not a judgement on your report.
- Small, self contained reports get answered first, because they can be acted on
  in one sitting.

If a report is closed without a fix, the reason will be written in the thread.

## The projects

| Project | Kind | What it is |
| --- | --- | --- |
| Vaelora Velocity | Unreal Engine 5 | Rocket Racing, rebuilt from the ground up. |
| LUX3 | UEFN | Every sunset track, brought back to the light. |
| The Reality Cross | UEFN Event | The moment Vaelora Velocity left the Fortnite Loop. |
| Meridian | Server software | An original re-implementation of the network services an archived Fortnite build expects. Early, in development. |
| Website | visionforceofficial.com | The public roadmap and voting site. |

## Reporting a bug

Open a bug report through the issue form. Before you do, two checks that save
everyone a round trip:

1. Search the open and closed issues for the same symptom.
2. Confirm it still happens on the current build.

A good report answers four things: what you did, what you expected, what
happened instead, and how often it repeats. Exact numbers beat adjectives, so
"the car loses about half its speed on any wall contact" is worth more than "the
collisions feel wrong". Attach a log if you have one. A short clip helps for
anything about feel or timing.

Never paste anything into an issue that you are not free to share, including
account credentials, tokens, or private build files.

## Proposing a feature

Feature ideas belong in one of two places.

- Gameplay and roadmap ideas: post them on the public roadmap at
  <https://visionforceofficial.com>, where they can be voted on. That vote is
  what decides build order.
- Changes to code, tooling or documentation in a Vision Force repository: open a
  feature request through the issue form here.

Start with the problem, not the solution. Describe what is awkward today, who it
affects, and what you tried instead. A proposal that names its own trade offs is
far more likely to be picked up than one that only lists benefits.

## Sending a change

There is no obligation to send code. If you want to:

1. Open an issue first for anything larger than a typo, so the direction can be
   agreed before you spend time.
2. Fork, branch, and keep the change to one subject.
3. Open a pull request and fill in the template.

Branch names:

```
feat/short-subject      new behaviour
fix/short-subject       a defect
docs/short-subject      documentation only
chore/short-subject     build, tooling, formatting
```

Commit messages: a short imperative summary on the first line, under about 72
characters, then a blank line, then the reasoning if it is not obvious.

```
fix: keep the drift boost charge across a respawn

The charge was reset on pawn possession, which also fires on respawn.
```

Match the style of the file you are editing rather than reformatting it. A
formatting sweep mixed into a behaviour change makes the behaviour change
impossible to review.

## The rule that has no exceptions

**No Epic Games code or assets in any contribution.** That means no decompiled
or copied source, no engine or game files, no extracted meshes, textures, audio,
maps or configuration, and no material derived from a leaked build. This applies
to pull requests, issue attachments, and links posted in threads.

Meridian is an original re-implementation of network services. It does not
contain, ship or redistribute Epic Games code or assets, and it never will.
Players bring their own archived client. Do not post client downloads or links
to them in any Vision Force space.

Vision Force Studio is not affiliated with or endorsed by Epic Games. Fortnite
and Unreal are trademarks of Epic Games, Inc.

## Conduct

Everything here is covered by the [Code of Conduct](CODE_OF_CONDUCT.md). Reports
go to contact@visionforceofficial.com.

## Getting help

See [SUPPORT.md](SUPPORT.md). For a security issue, do not open an issue, follow
[SECURITY.md](SECURITY.md) instead.
