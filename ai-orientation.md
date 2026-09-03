---
author: @ben-pr-p
status: Draft
---

# AI Orientation

AI assistance is an accepted and essential component of productive modern software development, and "spare tokens" 
from frontier coding models that NYC-DSA members may have via subscriptions are an important way to support the work we do.

However, AI usage creates a number of conflicts and contradictions for a socialist organization. 
Other documents ([guidelines for direct chapter use of AI](https://docs.google.com/document/d/1iyyYbBmagNeTsvM3NlC56hLa_xcSMtzYHbsvpU0Vm1o/edit?tab=t.0), [adopted resolution on use of AI in creative domains](https://docs.google.com/document/d/16DKpTR0R2IW2yrdDHoRNmVIKKO0OcMwCnX96zWcIGD4/edit?tab=t.qltocyokwtgk#heading=h.uj0yw3evpgsy)) are
governing/orienting documents for use of AI in other work of the organization. This document is about
how contributors should use coding agents in their capacity as Tech & Tools contributors.

In Tech & Tools, we are primarily concerned with how AI can degrade the welcoming and collaborative
culture we strive to create.

The following are some some principles and a handful of redlines to guide how members use AI:

# Principles

## *"Just send me the prompt"* (try to write yourself)

> See blog post from [George Kettleborough](https://blog.gpkb.org/posts/just-send-me-the-prompt/).

Sending a fellow NYC-DSA member written communication is an imposition on their individual time and on the collective resource
of "the spare time we all, as volunteers, have to devote to DSA". 
Using AI in your communication creates a substantial risk of  wasting someone's time. At the very least, 
you should review the content of written communication and ensure that it is something that *you* 
would think it is worth your time to *read*.

This means that *in general*, documentation, project updates, proposals, and messages to other 
contributions should probably be hand-written.

**Exceptions**:
- *Documentation intended to be minimally by humans (agentic development artifacts)*: if you are having a coding 
  agent work through a problem with an instruction like "Write a log of bugs found and fixed to DISCOVERY.md". 
  This writing may be a method of passing context between different coding sessions or just a stored conversation output,
  and will only be read by a human to debug something or out of curiosity.
- *Writing generated with unique access to specific context*: consider the output of "Benchmark this job with a variety of
  different batch sizes on my machine and write a summary of your findings to BENCHMARK.md". Such a file would be 
  writing produced with unique experience that may be impossible or expensive for others to reproduce. If you just shared
  the prompt, they may struggle to reproduce the result with the tools available to them. This is okay!

## *"Your job is to deliver code you have proven to work"*

> See blog post from [Simon Willison](https://simonwillison.net/2025/Dec/18/code-proven-to-work/).

This applies whether you wrote it by hand or with an LLM:
- You should prove the change works before you ask someone else to look at it
- Dumping a giant untested PR on reviewers is rude
- Prove it however fits: run it yourself, add tests, paste commands/output or a short screen capture in the PR
- A computer can't be held accountable; the human who opened the PR can

If you're in a situation where you want to hand off an in progress task with unreviewed generated code, just
*say so*. It's fine, good, and better to admit you used AI and what the current status of the code is than
to place a comrade in the position of cleaning up after you, likely without your original conversation context
and on their dime.

## Be honest about your usage 

It's okay to use AI to use AI to generate code, and it's neither okay nor socially necessary to hide it.

Honesty is important: your relationship to the code you are sharing will change how others interact with
you about your work and being clear about that will help your collaboration work better.

If your code contains some bad technical decisions or other problems which were created by AI with little
understanding from you, the social interaction between contributors around these questions is much easier 
if the reviewer/corrector understands that they are correcting your agent rather than correcting you.

## *Adding code is an imposition on an unknown future comrade*: accept rejection of your contributions on that basis

Three things are true:
  1. The fact that you were able to generate code which has utility in this moment is a different question  
     from the Tech & Tools committee's evaluation of the utility and liability of the code over its expected lifetime
  2. The Tech & Tools committee treats shipping code as carrying a commitment to the members of NYC-DSA that we will
     maintain the volunteer and committee structures to ensure the software continues to work and can evolve as our members' needs change.
  3. As an individual with a complex life, you cannot commit to indefinite maintenance of a piece of software in a volunteer
     capacity.

Because of these three, it is possible that certain contributions could be rejected or deferred if people think 
it would be unreasonable to expect a future Tech & Tools contributor to maintain it. This could because of its quality
(horrific slop that still works) or its complexity even if it is high quality (we are not going to maintain, like, a database).

## Project ownership is about more than coding, AI won't help that much - we plan capacity accordingly

As we try to build more capacity in the Tech & Tools Committee, most of the capacity we need to build is unrelated to
the actual output of code.

Our most precious resource to cultivate and allocate is socialist organizers who know how to communicate about and
use and build software to help solve the complex organizing challenges of their comrades.

How quickly one can generate code with AI is mostly unrelated to their capacity to own projects. The fact that 
coding is easier now *does not* mean we need fewer contributors. It's the opposite: since code is easier, we can be
more useful, and we need more contributors to be able to hold collaboration across the organization.

Being a project owner means being a partner and co-organizer with the users of our software. Project owners should
strive to maintain relationships and an understanding of the organizing goals and challengers of their collaborators
and users in the organization. AI shouldn't be used for this, and this is the bulk of the work of our committee!

## NYC-DSA is not interested in maintaining claims to intellectual property: use the subsidies!

NYC-DSA is not interested in maintaining any claims to specific intellectual property. Most of our repos are private
with an MIT license (technically open source but only discoverable by NYC-DSA members, and freely shared upon request with
DSA members from other chapters). 
Owning intellectual property and exercising claims is an annoying and risky thing for a member-driven socialist
organization incorporated as a 501c4 with very little upside.

Additionally, it's easier from a compliance perspective for our work with our endorsed electoral campaigns for
us to have no intellectual property claims on the code we share or run for them. If we did, sharing the software for them
may count as a contribution and be subject to regulation.

This means that you can use coding subscriptions with provider-friendly data retention policies such as Claude Code,
Codex, Meta Muse Spark 1.3 Contributor tier, or anything Chinese.

Don't worry about leaking the code or intellectual property - we don't want it!

# Redlines

## Member Data

Do not put member data that you may receive access to as part of your contributions as an input to 
calls to large language models, whether used via a coding agent or other API call.

Membership or activity in DSA is a sensitive piece of data that can carry real world professional or 
for our members. We have a responsibility to our fellow members to protect it.

By and large you should not have to worry about this (see [We never develop against prod data](principles.md#we-never-develop-against-prod-data)), but take care if you happen to be working with
real data.

## AI Generated Copy or Creative Assets

This is covered in [the Chapter's adopted resolution banned the use of AI in creative domains](https://docs.google.com/document/d/1iyyYbBmagNeTsvM3NlC56hLa_xcSMtzYHbsvpU0Vm1o/edit?tab=t.0), but software contributors should be careful 
to not violate this in the course of their work.

AI generated copy as part of an application flow, AI generated application branding, or other AI generated
decision oddities (use of emojis in place of proper icons, etc.) will undermine our members and the public's 
confidence in our work and damage the work our designers do.

We have a repo of branded [shadcn/ui](https://ui.shadcn.com) components that will allow you to use AI to generate
your code *without* accidentally bringing in AI's creative decisions.

We have excellent designers in the chapter who have succeeded in creating a powerful brand for New York City
which communicates the seriousness, boldness, and vision of our mission, and we should use their work!
