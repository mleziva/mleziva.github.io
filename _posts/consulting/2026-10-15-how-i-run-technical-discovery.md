---
title: How I Run Technical Discovery with Enterprise Customers
date: 2026-10-15 09:00:00 -0500
categories: [Consulting, Discovery]
tags: [consulting, discovery, architecture, agile, project management, customer engagement]
description: The goals, preparation, facilitation, and deliverables I use to run technical discovery with enterprise customers, plus the mistakes I see most often and a success story from a Fortune 500 engagement.
---

Most of the projects I have seen go sideways did not fail because of the code (some did, though that's becoming rarer as AI-assisted development improves). These projects failed in the first few weeks, when the team agreed to build something before anyone really understood the problem. A good technical discovery session is the best way to prevent those issues. It allows you to catch a lot of assumptions up front, not after multiple sprints.

Over 11 years of consulting, including my time at Microsoft and AWS, I have run discovery sessions and project kickoffs for customers ranging from small teams to Fortune 500 enterprises. This post walks through how I approach them: what the session is for, how I prepare, how I run the room, what I hand over afterward, and the mistakes I see most often. I'll finish with a story from an engagement where I led a team that embraced these techniques, and it paid off.

## What a discovery session is actually for

A discovery session is not a sales meeting and it is not a design review. Typically customers don't have a clear design at this point. The session has a handful of goals, and every part of the agenda should serve at least one of them.

### Establish rapport

People share the real story with people they are comfortable with. The polished version of a problem shows up in the RFP. The real version comes out when someone trusts you: the spreadsheet that holds the whole process together, the system nobody wants to touch, the integration that fails every month-end.

In-person kickoffs are by far the best way to build that comfort. Lunch, whiteboard time, and the conversations in the hallway between sessions do more for a relationship than a week of calls. When in person is not possible, I ask for **cameras on from the very first minute**, and I turn mine on first. It is a small thing, but it changes the energy of a remote session. Faces make it a conversation instead of a conference call.

### Build trust

Rapport gets people talking. Trust is what makes them believe you will act on what they tell you. I build it by doing exactly what I said I would do, in small ways and early. If I say I'll send the notes by end of day, they arrive by end of day. If I don't know something, I say so and follow up with the answer. Trust also comes from being honest when an idea will not work, even when the customer is excited about it.

### Listen, and understand the problem before the solution

This is the most important goal and the one most often skipped. The objective is to understand the customer's problem **in their terms**: who feels the pain, how often, what it costs, and what they have already tried. When I think I understand it, I restate the problem back to them and keep adjusting until they say, "Yes, that's it."

What I deliberately avoid is fitting our solution to their problem. Every consultant walks in with a favorite architecture, a familiar service, or a reference implementation from the last engagement. Those are useful later. In discovery, they are a filter that makes you hear only the parts of the problem your solution already solves.

### Ask probing questions

Good discovery questions are open-ended, specific, and grounded in real events. A few I return to often:

- "Walk me through the last time this went wrong. What happened, step by step?"
- "Who feels this pain the most, and what do they do about it today?"
- "What have you already tried, and why didn't it stick?"
- "If we could fix only one thing, which would it be?"
- "How will you know, six months after launch, that this worked?"
- "What would make you cancel this project?"

When an answer is vague, I keep asking "why" until it isn't. The [five whys](https://en.wikipedia.org/wiki/Five_whys) technique is simple, but it reliably gets from a symptom ("deployments are slow") to a cause ("every release needs a manual sign-off from a team in another time zone").

### Leave with a plan, next steps, and a shared vision

A session that ends with good conversation and no plan was not a success. By the end, I want three things:

1. **A shared vision** that everyone in the room can describe in roughly the same sentence.
2. **A plan** to get there, at the level of milestones rather than tasks.
3. **Next steps** with named owners and dates.

## Before the session

Preparation decides how much of the session goes to real discovery and how much goes to basic orientation. I prepare four things.

### Stakeholder map

I map everyone who influences the outcome, not just the people on the invite. For each person I note their role, what they care about, and what I need from them.

| Role | Typical concern | What I need from them |
|---|---|---|
| Executive sponsor | Business outcome, cost, timeline | The "why", success criteria, decision authority |
| Product owner / business lead | Features, users, priorities | The vision, priorities, availability for daily collaboration |
| End users | Day-to-day workflow | How the work actually gets done today |
| Engineering / IT lead | Fit with existing systems, maintainability | Current architecture, technical constraints, team skills |
| Security and compliance | Risk, policy, audit | Non-negotiable controls and approval process |
| Operations / support | Who gets paged at 2 a.m. | Monitoring, support model, operational pain |

The people who most often get missed are security, compliance, and operations. They rarely sponsor a project, but any one of them can stop it late in the game. I would much rather hear their concerns in week one than in the week before go-live.

### Pre-read request

I send the customer a short list of materials to share ahead of time. I keep it short on purpose, because a long list delays the session or gets ignored.

- Current architecture diagrams, even rough or outdated ones
- Process documentation or a description of the workflow in scope
- Any existing roadmap, backlog, or requirements
- Security, compliance, and data-handling policies that apply
- Notes on any previous attempt to solve this problem

Outdated diagrams are useful too. The difference between the diagram and reality is often where the interesting problems are.

### Initial assumptions

Before the session I write down what I *think* is true: the likely problem, the likely constraints, and the likely shape of a solution. I write these as statements to test, not conclusions. During the session, I confirm or discard each one. Writing them down keeps me honest. If I never wrote down my assumptions, I'm much more likely to treat them as facts.

### Question list

I organize my questions by area so I don't lose coverage when the conversation goes somewhere unexpected (which it should):

- **Business:** goals, drivers, success metrics, timeline pressure, budget
- **Users:** who they are, how many, what they do today, what frustrates them
- **Process:** the end-to-end workflow, handoffs, manual steps, exceptions
- **Technology:** current systems, integrations, hosting, tooling, technical debt
- **Data:** sources, ownership, quality, volume, sensitivity
- **Security and compliance:** identity, network boundaries, regulatory requirements, approval processes
- **Delivery:** team structure, skills, availability, how decisions get made

### Get the customer's ideas flowing

I also send the customer one question to think about ahead of time: **"What is your vision for this?"** Sometimes I frame it as, "Imagine it's eighteen months from now and this project was a huge success. What's different?" Customers who have thought about that question before the session show up with energy and ideas instead of waiting to be told what to do.

### When the customer doesn't have a clear vision

Often the honest answer to the vision question is, "We're not sure." That is normal and it is fine. It just means the session needs a different shape. In that case, I take whatever information we have and plan a **brainstorming session** where everyone in the room is empowered to share ideas.

How I run it:

1. **Frame the problem** in one or two sentences everyone agrees on.
2. **Generate ideas silently first.** Everyone writes ideas on sticky notes (real or virtual) for a few minutes before anyone speaks. This keeps the most senior or loudest person from setting the direction before others have thought for themselves.
3. **Share every idea** without judging it. Quantity over quality at this stage.
4. **Group similar ideas** into themes.
5. **Vote.** Each person gets a few dot votes to place on the themes they think matter most.
6. **Discuss the top themes** in depth, which turns them into the starting point for the vision.

Some of the best ideas I have seen came from the person in the room with the least seniority and the most hands-on experience with the problem. The process exists to make sure those ideas get heard.

## Running the session

### Start with an agenda and define success

I share the agenda in advance and walk through it at the start. More importantly, the first agenda item is agreeing on **what will make this session a success**. I write those outcomes on the whiteboard where everyone can see them. Here is a typical full-day agenda:

| Block | Purpose |
|---|---|
| Introductions | Names, roles, and what each person wants out of the day |
| Session goals | Agree on what "success" means for today and write it down |
| Vision and business drivers | Why this project, why now, what success looks like long term |
| Current state walkthrough | Map the existing systems and processes on the whiteboard |
| Live system demo | See the real systems and workflows in action |
| Pain points | What's broken, who it affects, and what it costs |
| Constraints | Security, data, compliance, budget, timeline, skills |
| Future state / brainstorming | Shape the vision and the first version |
| Recap and next steps | Read back decisions, open items, owners, and dates |

During the day, I go back to the success criteria at natural breaks. "We're breaking for lunch. We've covered two of our four goals, and the afternoon needs to focus on constraints and next steps." Anything important that doesn't fit goes into a visible **parking lot** with an owner, so it doesn't derail the session or get lost.

### Map the current setup on the whiteboard

I draw the current state live, with the customer correcting me as I go: systems as boxes, data flows and integrations as arrows, people and teams at the points where they touch the process. Manual steps get special attention, because they usually point to the biggest pain. Drawing it together is faster than reading documents, and the customer's corrections ("no, that file actually goes through Bob's inbox first") are where the real discovery happens. I photograph or digitize the board before anyone erases it.

### Dig into pain points and success metrics

For each pain point I try to capture **who** it affects, **how often**, and **what it costs** in time, money, errors, or customer impact. Then I connect pain points to success metrics: if this is the problem, what number moves when we fix it? I also ask how that number is measured today. A success metric without a baseline is hard to prove later.

### Surface constraints early

Constraints are not obstacles to work around later. They shape the design from day one.

- **Security:** identity provider, network boundaries, encryption requirements, third-party access rules
- **Data:** where it lives, who owns it, its quality, its volume, and how sensitive it is
- **Compliance:** the regulations and internal policies that apply (for example SOX, PCI DSS, HIPAA, or data residency rules) and the approvals required before go-live
- **Organizational:** budget, deadlines, change freeze windows, and the skills of the team that will own the system long term

### Ask to see the real systems

Documentation describes how a system is supposed to work. Watching someone use it shows how it actually works. I always ask the customer to show me the real systems, and when possible, to let me use them myself with a test account. I also ask what similar products or competitors they admire, and we look at those together. If there are existing systems or similar products, seeing and using them is crucial. A five-minute demo routinely turns up workarounds, edge cases, and frustrations that never made it into any document.

### Close the loop

The last block of the day is the most important one. I read back the decisions we made, the open questions with their owners and due dates, and the agreed next steps. Then I check the result against the success criteria we wrote on the board that morning. If we missed one, we say so and schedule the follow-up before anyone leaves.

## What I hand over afterward

I send the deliverables while the session is still fresh, while people still remember the details and the momentum is still there. The package typically includes five items.

### Discovery report

A concise summary of what we learned: the problem statement in the customer's words, the current-state diagram, pain points, success metrics with baselines, constraints, the agreed vision, and the open questions. This is the document the sponsor forwards to their leadership, so it needs to make sense to someone who wasn't in the room.

### Architecture decision records

Every significant technical decision made or proposed during discovery gets an **architecture decision record (ADR)**, a format described by [Michael Nygard](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions). Each ADR is short and has four parts:

- **Context:** the situation and the forces at play
- **Decision:** what we chose to do
- **Status:** proposed, accepted, or superseded
- **Consequences:** what becomes easier or harder because of this choice

ADRs are valuable because six months later, when someone asks "why did we do it this way?", the answer is written down along with the constraints that made it the right call at the time.

### Risk register

A simple table of what could go wrong, how likely and damaging it is, and who owns the mitigation.

| Risk | Likelihood | Impact | Owner | Mitigation |
|---|---|---|---|---|
| Key integration partner's API is undocumented | High | High | Customer IT lead | Request sandbox access and a technical contact before sprint 1 |
| Security review takes longer than the release schedule allows | Medium | High | Delivery lead | Engage security in week one and review the design early |
| Product owner has limited availability | Medium | Medium | Executive sponsor | Assign a dedicated delegate with decision authority |

### Prioritized backlog: milestones and big rocks

The end goal is broken down into **milestones**, each one a meaningful step the business can see and validate. Each milestone is then broken down into **big rocks**: the large chunks of work that have to happen to reach it. (The term comes from Stephen Covey's idea that if you don't put the big rocks in the jar first, they won't fit later.)

For example, a milestone like "customers can pay an invoice online" might break down into big rocks such as invoice data integration, a payment provider integration, a customer-facing portal, and notifications.

At this stage we deliberately **have not written user stories yet**. That is the next step, and it is done together with the product owner and the engineering team, not handed down by the discovery team.

### Scope of the first version

Finally, I define what goes into the first release, and just as importantly, what is explicitly **out** of it. A written "not in version one" list prevents a lot of scope creep and a lot of awkward conversations later.

## Common mistakes I've seen

Over 11 years, the same few mistakes come up again and again.

### Not listening to the customer

It sounds obvious, but it is the most common failure. The consultant spends the session presenting instead of asking, or hears the first few sentences of a problem and starts solving it. A good rule of thumb is that the customer should be doing most of the talking in a discovery session. If I notice that I am the one talking most, I stop and ask a question.

### Selling a pre-defined package

Many consulting organizations have standard offerings, and they are useful when they fit. The mistake is walking into discovery already committed to one, then bending the customer's requirements until they fit the package. The customer ends up with a solution to a problem they don't have, and the problem they do have is still there. Discovery should decide the solution, not confirm one that was picked before the meeting.

### Not defining the goals of the discovery session

Without clear goals for the session itself, discovery turns into a series of interesting conversations that end with many half-baked threads and nothing concrete. Everyone leaves feeling it went well, and a week later nobody can say what was decided. Writing down the session's success criteria at the start, and checking back against them throughout the day, is the simplest fix I know.

### Spending too much time on design

The opposite failure is a discovery phase that never ends: months of diagrams, documents, and reviews before anyone builds anything. Design is cheap compared to rework, but it is expensive compared to learning. Some questions can only be answered by building something and putting it in front of users. My approach is to **start fast, fail fast, and iterate fast**. Do enough design to make the important decisions, then build the smallest thing that tests the riskiest assumption.

## Success story: a cloud-native B2B invoicing and payments platform

### The customer and the idea

A Fortune 500 customer came to us with a novel idea: connect invoicing and payments in a single business-to-business platform, built entirely in the cloud. The idea was strong, but the customer had very little experience building software, and even less with the cloud. This was around 2018, when the cloud was well established. The customer came to Microsoft for its expertise and guidance and wanted the platform to run on Azure.

### Introducing a new way of working

Because the customer was new to software delivery, a big part of the engagement was introducing **project management and agile development**. We didn't just bring a methodology and expect them to adopt it. We explained the reasons behind each practice and adjusted it as we learned how their organization worked.

We formed **feature teams** that each owned a slice of the product end to end, which allowed us to build features in parallel instead of passing work through a single bottleneck. To keep those teams aligned, we held **daily meetings between product and developers**. Those meetings were where priorities were confirmed, questions were answered before they became blockers, and small course corrections happened before they turned into big ones.

### My role

I led the feature teams. I set the technical vision for the platform, and I also kept insight into all of the product's functionality, not just the architecture. That combination mattered. Because I understood both the business behavior and the technical design, I could spot when a product decision had a hidden technical cost, or when a technical shortcut would change what the user experienced.

### Constant communication

The key to achieving the customer's goals was constant communication. Tickets were never just "kicked over the fence" from product to engineering. **Writing the user stories was a collaboration between product and tech.** Product brought the business intent, engineering brought the constraints and options, and the stories we wrote together were clearer, smaller, and far less likely to be misunderstood.

### Focusing on what mattered most

We achieved efficiency by prioritizing features that were both **the most important to the business and the lightest lift to implement**. When we mapped the backlog on a simple value-versus-effort grid, the upper-left quadrant became our starting point:

| | **Low effort** | **High effort** |
|---|---|---|
| **High value** | Build first | Plan carefully, break into smaller pieces |
| **Low value** | Fit in when convenient | Defer or drop |

That gave the customer working, valuable software early, which built their confidence in both the platform and the new way of working.

### Scaling with managed PaaS services

To speed up the time to go live, we built on **managed platform-as-a-service (PaaS)** offerings in the cloud. Using managed services meant the team had no virtual machines to patch or operating systems to maintain, and scaling was handled by the platform rather than by the team. For a customer with little cloud operations experience, removing that operational burden was as important as the speed it gave us.

The solution was built on Azure App Service. An Azure SQL Database was the central source of truth, replicated across several regions. We used Azure Active Directory and Azure AD B2C to build out the identity system, relying on well-tested services instead of building our own.

### The outcome

The customer was happy with the result. Over the course of the project, their vision changed and the product evolved with it, and that was a good thing. A rigid plan written in the first month would have delivered what they *thought* they wanted. Because we started with good discovery, kept product and engineering in constant contact, and worked iteratively, we delivered what they actually needed as their understanding grew.

As with any good consulting project, the goal is to transition it over to the customer. As their number of users grew into the thousands, more of my time was focused on ramping up customer engineers, providing guidance and documentation while my hands-on-keyboard time was reduced. 

## Key takeaways

- **Discovery is about understanding the problem**, not presenting a solution. Listen more than you talk.
- **Prepare thoroughly**: map stakeholders, request pre-reads, write down assumptions, and organize your questions.
- **Ask for the vision up front**, and when there isn't one, run a brainstorming session where everyone can contribute.
- **Define what success looks like for the session** and check against it throughout the day.
- **See the real systems.** Demos reveal what documents don't.
- **Hand over concrete artifacts**: a discovery report, ADRs, a risk register, milestones broken into big rocks, and a clear first-version scope.
- **Move quickly from design to building**, and expect the vision to evolve. That's a sign the process is working.
