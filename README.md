# Storytelling Framework

> **Help AI understand the story before it starts polishing the sentences.**

This repository contains a modular storytelling framework designed to work with ChatGPT.

It is more than a collection of prompts. It is a small decision engine that classifies a storytelling request, chooses the right workflow, loads the principles needed for that workflow and checks the result against a shared quality standard.

The framework is hosted on GitHub so its instructions can be maintained, reviewed and improved in one place. ChatGPT is connected to it by pointing your ChatGPT profile or Project instructions at the router:

```text
https://github.com/rstebbens/storytelling/blob/main/prompts/00-router.md
```

The router becomes the front door. Everything else follows from there. 🚪

---

## 📖 What does this do?

AI writing tools often move too quickly.

Give them a meeting transcript, a memory or a rough idea and they may immediately produce a polished article. The sentences can sound competent while the actual story remains uncertain. Important context gets smoothed over, plausible details appear without evidence and the author's voice slowly dissolves into generic prose.

This framework changes the order of operations.

Before writing, ChatGPT is asked to determine what kind of help is actually needed.

The user may be:

- trying to find the story inside an experience
- ready to turn developed notes into a first draft
- asking whether an existing story works
- requesting specific edits
- shaping something that will be spoken aloud
- working from a transcript that needs to remain recognisably human

Those requests require different kinds of thinking. The router separates them before the work begins.

The framework then applies shared principles around discovery, atmosphere, narrative, reflection, voice, editing and common AI writing patterns.

The result should be writing that is clearer, more authentic and more memorable without becoming artificially dramatic or suspiciously polished.

---

## 🧠 The core idea

Most prompt libraries are shelves full of independent instructions. You choose one, paste it into a conversation and hope it contains everything required.

This repository uses a layered architecture:

```text
                 User Request
                       │
                       ▼
              Intent Classification
                 prompts/00-router.md
                       │
       ┌───────────────┼────────────────┐
       ▼               ▼                ▼
    Discover        Critique          Write
       │               │                │
       └───────────────┼────────────────┘
                       ▼
          Shared Storytelling Principles
                       │
                       ▼
           Conditions of Satisfaction
                       │
                       ▼
                 Final Response
```

Each layer has one job.

### 1. The router decides what work is needed

`prompts/00-router.md` is the entry point.

It reads the user's intent rather than relying only on the wording of the request. It considers whether a story already exists, whether the user is exploring, asking for feedback, requesting changes or preparing something for spoken delivery.

The router does not write the story. It selects the workflow most likely to help.

### 2. The workflow explains how to do that work

Once the route has been chosen, ChatGPT opens the relevant workflow prompt.

A discovery workflow explores the event, people, atmosphere and meaning. A critique workflow evaluates an existing draft without silently replacing it. A writing workflow creates a draft only after the story is sufficiently understood.

Keeping these workflows separate reduces instruction leakage. Critique does not automatically become rewriting, and the presence of notes does not automatically trigger prose.

### 3. Shared principles define the standard

Each workflow names the principle files it depends on.

Those principles contain reusable guidance for subjects such as:

- discovering the real story
- building atmosphere from authentic details
- creating narrative movement
- allowing reflection to develop naturally
- preserving the author's voice
- editing without sanitising
- avoiding repeated AI rhythms and manufactured contrast

The workflow must load those dependencies before continuing. They are part of the workflow rather than optional background reading.

### 4. Conditions of Satisfaction act as the quality gate

Generating a response does not automatically mean the work is finished.

The framework uses a Conditions of Satisfaction document to check whether the result meets the expected standard. This creates a final pause for quality before the response reaches the user.

The router decides. The workflow directs. The principles guide. The conditions check. ✅

---

## 🗂️ Repository structure

The framework is organised into two main areas:

```text
storytelling/
│
├── prompts/
│   ├── 00-router.md
│   ├── discover-the-story.md
│   ├── write-the-story.md
│   ├── critique-a-story.md
│   ├── edit-a-story.md
│   └── other specialist workflows
│
├── principles/
│   ├── core principles
│   ├── discovery
│   ├── atmosphere
│   ├── narrative
│   ├── reflection
│   ├── voice and editing
│   ├── anti-patterns
│   └── conditions of satisfaction
│
└── README.md
```

### `prompts/`

This directory contains the router and task-specific workflows.

A prompt file should describe one coherent activity. It may define readiness checks, working steps, expected outputs and the principle files that must be loaded.

### `principles/`

This directory contains reusable standards shared by several workflows.

A principle should remain broadly applicable. Workflow-specific sequencing belongs in a prompt file rather than being hidden inside a shared principle.

### `README.md`

This document explains the framework to people. The prompt and principle files explain the framework to the AI.

---

## 🔄 How a request moves through the framework

The framework is easiest to understand through examples.

### Example 1: The story has not been found yet

The user says:

> I had a difficult meeting yesterday. There might be a story in it, but I am not sure what it is really about.

The request should move through the system like this:

```text
1. ChatGPT begins with prompts/00-router.md.
2. The router identifies an idea with an unclear narrative centre.
3. It selects prompts/discover-the-story.md.
4. The discovery workflow loads its named principles.
5. ChatGPT explores what happened, who mattered and what changed.
6. Material uncertainties become questions rather than invented details.
7. The workflow ends with either Ready to write or Continue discovery.
```

The framework protects the user from receiving a premature article about the wrong story.

### Example 2: An existing draft needs feedback

The user says:

> Here is the finished story. Does it work?

The route becomes:

```text
1. The router recognises an existing story and a request for evaluation.
2. It selects prompts/critique-a-story.md.
3. The critique workflow loads its dependencies.
4. ChatGPT identifies the story and evaluates how effectively it is told.
5. It highlights the highest-leverage improvement.
6. It does not produce a replacement draft unless the user asks for one.
```

### Example 3: The user has accepted a specific change

The user says:

> Apply your recommendation to the ending, but leave the rest alone.

The router should select the editing workflow. The edit remains bounded by the user's instruction and protects the existing voice.

### Example 4: The material will be spoken

The user says:

> Turn this into a ten-minute talk that sounds natural when read aloud.

The story may first need discovery, critique or writing. Once the story itself is sound, the relevant spoken workflow can shape cadence, breath, emphasis and delivery.

Written-page standards should not be applied blindly to speech.

---

## 🧭 Available workflows

The repository can grow over time, but the central workflows currently follow this pattern.

### Discover the story

Use discovery when the user has an event, memory, transcript or idea but the narrative centre remains uncertain.

Discovery explores:

- what actually happened
- what changed
- why the event matters
- who matters within it
- what people believed or assumed
- what the environment felt like
- what the audience should remember
- which single message the story should carry

A successful discovery should produce a clear story, intended audience, dominant message, remaining questions, confidence rating and readiness recommendation.

Discovery should not quietly turn into a finished draft.

### Write the story

Use the writing workflow when discovery is complete and enough context exists to write without inventing material details.

The workflow confirms the story before building the scene, allowing events to unfold and developing the reflection. It protects personality, humour, awkwardness and emotional truth where those qualities belong to the author.

Its purpose is to tell the strongest version of a story that has already been found.

### Critique a story

Use critique when the user supplies an existing story and asks whether it works, what is missing, why it feels flat or whether it is ready to publish.

Critique examines areas such as:

- discovery
- atmosphere
- narrative
- reflection
- authenticity
- voice
- clarity
- memorability

It identifies the largest opportunity before producing a catalogue of smaller observations.

Critique is evaluation. It should not become an unsolicited rewrite.

### Edit a story

Use editing when the user wants an existing story changed or has accepted specific critique recommendations.

Editing may tighten, shorten, restructure or refine the work while preserving the author's voice and intent.

When the user only says “make this better” and the real weakness has not been established, the framework should critique before editing.

### Speech and spoken transcript workflows

Spoken material needs room to breathe.

These workflows account for cadence, delivery, natural phrasing, emphasis and the difference between language that reads well on a page and language that sounds credible aloud.

When working from transcripts, the objective is to sharpen the speaker's meaning without turning natural speech into corporate copy.

---

## ✍️ The storytelling principles

The principles provide the shared philosophy behind the workflows.

### Discovery before drafting

An event is not automatically a story.

The first account may describe what happened. Deeper exploration can reveal what the people involved believed, feared, misunderstood or learned. The strongest version often emerges after the obvious version has been challenged.

### Atmosphere from authentic detail

A story needs a place, a moment and a feeling.

Atmosphere comes from concrete observations that are known to be true: the room, the sound, the number of people, the mood beforehand or the small detail everyone remembered later.

The framework does not manufacture cinematic scenery simply to make an event appear important.

### One dominant message

A story can contain several observations, but the reader should leave with one main idea.

Supporting material earns its place by strengthening that idea. Competing lessons dilute it.

### Natural narrative movement

Narrative is more than a sequence of events. Something must change in understanding, behaviour, expectation or circumstance.

The framework avoids forcing every experience into a theatrical rise, collapse and triumphant resolution. Real stories are allowed to remain awkward, incomplete or unresolved.

### Reflection creates meaning

The framework does not sprint from conflict to a packaged lesson.

Reflection explores why people behaved as they did, what assumptions were operating and what only became visible afterwards. Meaning should develop from the events rather than being attached as an explanatory label at the end.

### Voice over polish

The author should remain recognisable.

Editing should sharpen rather than sterilise. Humour, doubt, contradictions and unusual phrasing may carry more truth than a perfectly smooth paragraph.

The aim is for the author to sound like themselves on a very good day.

### Protection against AI anti-patterns

The framework actively looks for patterns that make writing feel assembled:

- repetitive short declarations
- manufactured contrast
- repeated negation
- stacked rhetorical questions
- generic business language
- predictable paragraph rhythms
- excessive explanation
- artificial drama
- conclusions that announce what the reader already understands

These patterns are removed because they distract from the story, not because every sentence must follow a rigid style rule.

---

## ⚙️ Connecting the framework to ChatGPT

There is no application to install and no code to run.

GitHub hosts the current instruction files. ChatGPT is told where the framework begins.

```text
ChatGPT profile or Project instruction
                  │
                  ▼
Public URL to prompts/00-router.md
                  │
                  ▼
Router selects the workflow
                  │
                  ▼
Workflow loads named dependencies
                  │
                  ▼
ChatGPT completes the request
```

### Option 1: Use a ChatGPT Project

This is usually the cleanest setup when you want the framework to apply only inside a dedicated storytelling space.

1. Create or open a ChatGPT Project.
2. Open the Project instructions.
3. Add the following:

```text
For every storytelling request, begin with this framework router:

https://github.com/rstebbens/storytelling/blob/main/prompts/00-router.md

Read the router and determine the correct workflow from the user's intent.
Open the selected workflow and load every repository file named as a dependency before continuing.
Treat the repository files as the current source of truth.
Do not assume their contents from a previous conversation.
If missing context could materially change the story, ask questions before writing.
```

4. Save the instructions.
5. Start a new conversation inside the Project.

### Option 2: Use ChatGPT profile instructions

Use profile instructions when you want the framework available across conversations rather than inside one dedicated Project.

Add something similar to:

```text
When I ask for help discovering, writing, critiquing or editing a story, use this repository as the storytelling framework:

https://github.com/rstebbens/storytelling/blob/main/prompts/00-router.md

Begin with the router, select the appropriate workflow and load every dependency named by that workflow before responding.
Use the repository as the current source of truth.
```

Profile-level instructions have wider reach, so ChatGPT may apply the framework whenever a request appears to involve storytelling.

### What “connected” means

The connection is instruction-based.

This repository does not:

- install a ChatGPT extension
- create a custom model
- use GitHub Copilot instructions
- call the OpenAI API
- execute software
- receive or store your conversations

ChatGPT is simply directed to read a public GitHub document and follow the references contained within it.

---

## 🧪 Testing that it works

Start a new conversation in the configured Project or profile and try:

> I have a memory about a meeting that changed how I think about leadership, but I do not yet know what the story is. Which route should we use?

A correctly routed answer should select discovery rather than immediately producing a finished story.

You can also ask:

> Which repository workflow did you select, and which dependencies did you load?

That question is useful when validating a new setup or troubleshooting an unexpected response.

Further tests:

| Test request | Expected route |
| --- | --- |
| “There might be a story in this.” | Discover |
| “Turn these developed notes into a first draft.” | Write, provided discovery is complete |
| “What do you think of this story?” | Critique |
| “Is this publishing ready?” | Critique |
| “Apply the changes you recommended.” | Edit |
| “Shorten this by 20% without losing my voice.” | Edit |
| “Make this work as a ten-minute talk.” | Story workflow, then speech |
| “Review this transcript for cadence.” | Spoken transcript workflow |

---

## 🛠️ Extending the framework

The architecture is designed to grow without turning into one enormous prompt.

### Adding a new workflow

1. Create a focused Markdown file in `prompts/`.
2. Define the purpose of the workflow.
3. Explain when it should and should not be used.
4. Name every principle file it depends on.
5. Define its steps and expected output.
6. Add a Conditions of Satisfaction check where appropriate.
7. Update `prompts/00-router.md` so the new intent can be recognised.
8. Add routing examples and test ambiguous cases.

A workflow should perform one coherent kind of work. Avoid building a universal prompt that discovers, writes, critiques and edits in one pass.

### Adding a new principle

A principle should be reusable across workflows.

Good candidates include standards for dialogue, character, humour, long-form structure or research-backed storytelling.

Before adding one, ask:

- Is this guidance shared by more than one workflow?
- Does it describe a standard rather than a sequence of steps?
- Will changing it in one place improve several workflows?
- Does it duplicate an existing principle?

When a new principle is added, update the dependency lists of the workflows that genuinely need it.

### Changing the router

Router changes affect the entire framework and deserve careful testing.

Test requests with competing intents, such as:

- a draft that still lacks a clear story
- notes accompanied by a request to write immediately
- a request to “make this better” without identifying the weakness
- a speech that first needs narrative work

The router should choose the route that improves understanding before improving prose.

---

## 🎯 Design goals

The framework follows a few architectural goals.

### Single responsibility

The router routes. Workflows execute. Principles guide. Conditions validate.

### Explicit dependencies

A workflow states which principles it needs. Important guidance should not depend on assumed memory from earlier conversations.

### Reusable guidance

Shared principles live in one place so improvements can benefit several workflows.

### Intent before execution

The framework determines what the user is trying to achieve before selecting an action.

### Questions before invention

When missing context could materially change the story, the system should ask rather than create a plausible substitute.

### Voice before generic polish

Technical improvement is not useful when the author disappears from the page.

### Maintainability

New capabilities should be introduced through focused workflows and reusable principles rather than repeatedly expanding every existing file.

---

## 💬 Example ways to use it

### Explore an idea

> I keep thinking about something that happened during a workshop. Help me work out whether there is a story in it.

### Find the stronger story

> Here are my notes. Tell me what you think the obvious story is, then challenge it and look for a stronger one underneath.

### Prepare to write

> Summarise the story, audience, central change and single message. Tell me whether we are ready to draft.

### Write from discovered material

> We have completed discovery. Use the writing workflow to create the first draft in my voice.

### Critique honestly

> Review this as an editor. Identify the highest-leverage improvement and do not rewrite it yet.

### Edit deliberately

> Apply the critique to the middle section only. Preserve the humour and leave the opening unchanged.

### Shape spoken delivery

> This will be delivered aloud. Improve the cadence and flow without making it sound scripted.

---

## 🚧 Limitations

The framework improves the way ChatGPT approaches storytelling, but it does not remove every limitation of an AI assistant.

### Access to the repository

ChatGPT must be able to access the public GitHub files. When browsing or external access is unavailable, upload or paste the relevant router, workflow and principle files into the conversation or Project.

### Public repository

The framework files are public. Do not store confidential stories, internal transcripts, personal data or unpublished material in this repository.

Your source material belongs in your ChatGPT conversation or another appropriate private location. The repository should contain the reusable framework, not the stories it processes.

### Instruction adherence

AI responses can vary. A test request may occasionally be routed poorly or a dependency may be missed. Ask the assistant to state its selected route and loaded dependencies when behaviour seems unexpected.

### Authentic input still matters

The framework cannot discover details that were never supplied. Strong stories depend on real observations, memories, events and reflection.

It can help you find the questions. It cannot honestly invent the answers.

---

## ❓ Frequently asked questions

### Is this a GitHub Copilot project?

No.

GitHub is being used to host and version the Markdown files. The framework described here is intended to guide ChatGPT through a URL placed in ChatGPT profile or Project instructions.

### Why not paste everything into one large instruction?

A single instruction becomes difficult to navigate, maintain and test. It also exposes every task to guidance intended for every other task.

The router allows ChatGPT to load only the workflow and principles relevant to the current request.

### Why use GitHub?

GitHub provides version history, public access, reviewable changes, links between files and a familiar contribution model.

It also lets the framework evolve without requiring every user to manually replace a huge block of instructions each time one principle changes.

### Is this a custom GPT?

No. It can be used inside an ordinary ChatGPT Project or through profile instructions.

A custom GPT could use the same files, but one is not required.

### Can I fork and customise it?

Yes. Fork the repository, adjust the principles and point your ChatGPT instructions at the router in your fork.

### Can it be used with other AI assistants?

Potentially. Any assistant capable of reading linked Markdown files and following referenced dependencies could use the same pattern. Behaviour will vary by product and model.

### Does it write fiction?

The current framework is primarily designed around authentic stories, reflections, articles, speeches and lived experiences. Fiction-specific workflows could be added using the same architecture.

### Does it replace a human editor?

No. It makes the AI a more thoughtful participant in discovery, drafting and review. Human judgement remains central, particularly around truth, sensitivity, audience and what the author genuinely wants to say.

---

## 🗺️ Possible future directions

The framework can expand through additional workflows and principles, including:

- long-form essays and book chapters
- dialogue and character development
- case studies
- leadership stories
- presentations and keynote narratives
- humour and comic timing
- research-supported stories
- sensitive personal material
- story sequencing across a collection
- final publication review

New capabilities should preserve the existing architecture rather than turning the router into a writer or the principles into hidden workflows.

---

## 🤝 Contributing

Thoughtful contributions are welcome.

Useful contributions might include:

- clearer routing rules
- better ambiguity tests
- improvements to shared principles
- removal of conflicting or duplicated guidance
- additional workflow examples
- new specialist workflows
- corrections to broken paths or dependency references
- evidence that a prompt behaves differently from its stated intent

When proposing a change, explain:

1. What problem you observed.
2. Which layer owns the problem.
3. Why the proposed change belongs there.
4. Which workflows could be affected.
5. How the change was tested.

Try to improve the framework without flattening its central belief: better questions often produce better stories than earlier prose.

---

## 🌱 Final principle

The router exists to protect the story from premature prose.

Discovery comes before drafting.

Critique comes before unrequested rewriting.

Intent comes before execution.

Once the story is understood, the framework helps the writing carry it clearly, naturally and in a voice the author can still recognise.
