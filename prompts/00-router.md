# Storytelling Framework Router

This file is the entry point into the Storytelling Framework.

Every storytelling request should begin here.

Do not select a workflow arbitrarily.

First determine what the user is trying to achieve, then route the request to the most appropriate prompt.

---

# Step 1: Understand The Request

Identify the user’s primary intent.

Do not rely only on the exact words they use.

Consider:

* whether they already have a story
* whether they are still exploring an idea
* whether they want feedback
* whether they want changes made
* whether the content is intended to be spoken
* whether the story itself is clear enough to proceed

If the request is ambiguous, prefer the workflow that improves understanding before improving prose.

---

# Step 2: Select The Workflow

## Discover

Use:

`prompts/discover-the-story.md`

Choose this workflow when:

* the user has an idea but has not yet found the story
* the emotional or narrative centre is unclear
* important context is missing
* several possible stories appear to be competing
* the user asks what the real story might be
* the user wants help exploring an event, memory or experience
* the material contains facts but no clear change, meaning or message

Typical requests include:

* “I have an idea for a story.”
* “There might be something in this.”
* “What is the real story here?”
* “Help me work out what this is about.”
* “I want to tell a story about something that happened.”

Do not begin writing until discovery is sufficiently complete.

---

## Write

Use:

`prompts/write-the-story.md`

Choose this workflow when:

* the story has already been discovered
* the central event, change and message are understood
* the user explicitly wants a first draft
* enough context exists to write without inventing important details

Typical requests include:

* “Write this as a story.”
* “Turn these notes into a story.”
* “Create a first draft.”
* “Write this in my voice.”

If discovery is incomplete, route to `discover-the-story.md` first.

Do not compensate for missing context with polished invention.

---

## Critique

Use:

`prompts/critique-a-story.md`

Choose this workflow when:

* the user provides an existing story and asks for feedback
* the user asks whether a story works
* the user asks whether it is ready to publish
* the user asks for a score, review or assessment
* the user says the story feels flat, weak, unclear or overworked
* the user asks what should be cut, strengthened or explored
* the user asks for validation against the framework

Typical requests include:

* “What do you think?”
* “Critique this.”
* “Does this story work?”
* “Is this publishing ready?”
* “What is missing?”
* “Why does this feel flat?”
* “Review Story 12.”
* “Validate this against the repository.”

Do not rewrite the story unless the user explicitly asks for a rewrite after the critique.

If the underlying story has not been found, route to `discover-the-story.md`.

---

## Edit

Use:

`prompts/edit-a-story.md`

Choose this workflow when:

* the user wants an existing story changed
* the critique has already identified what needs improvement
* the user asks to tighten, shorten, restructure or refine the story
* the user asks for a revised version
* the user has accepted or selected specific critique recommendations

Typical requests include:

* “Apply those changes.”
* “Tighten the ending.”
* “Rewrite this section.”
* “Remove the repetition.”
* “Make the story flow better.”
* “Give me a revised version.”

Editing should preserve the author’s voice.

Do not sanitise personality, humour, awkwardness or emotional truth.

If the user asks to “make this better” without identifying what is wrong, critique before editing.

---

## Speech

Use the relevant speech-writing or spoken-transcript prompt when:

* the material will be spoken aloud
* the user wants a speech, talk, presentation script or spoken story
* cadence, breath, emphasis and delivery matter
* the user provides a transcript that needs shaping without losing natural speech

Choose between the available speech or transcript workflows based on the material provided.

Do not apply written-page standards blindly to spoken language.

---

# Step 3: Resolve Competing Intents

More than one workflow may appear suitable.

Use the following precedence rules.

## Existing Story And Feedback Requested

Route to:

`prompts/critique-a-story.md`

Do not rewrite immediately.

## Existing Story And Changes Requested

Route to:

`prompts/edit-a-story.md`

If the required improvement has not yet been identified, critique first.

## Idea Without A Clear Story

Route to:

`prompts/discover-the-story.md`

Do not write prematurely.

## Notes With A Clear Story And Explicit Draft Request

Route to:

`prompts/write-the-story.md`

## Story Intended For Speaking

Use the relevant story workflow first, then apply the spoken or speech workflow.

## Publishing Readiness

Route to:

`prompts/critique-a-story.md`

Publishing readiness is an evaluation task, not an editing task.

---

# Step 4: Load Dependencies

After selecting the workflow:

1. Open the chosen prompt.
2. Identify every dependency named in that prompt.
3. Load and apply those files before continuing.
4. Treat the dependencies as part of the workflow, not optional guidance.
5. Follow the Conditions of Satisfaction when the chosen prompt requires them.

Do not assume familiarity with repository principles from previous conversations.

Use the repository files as the current source of truth.

---

# Step 5: Protect Against Common Routing Errors

Do not route directly to writing merely because the user has supplied material.

Do not assume an event is already a story.

Do not rewrite when the user has asked for an opinion.

Do not edit before identifying the highest-leverage improvement.

Do not treat proofreading, critique and story discovery as the same task.

Do not invent context to avoid asking necessary questions.

Do not continue polishing when the underlying story remains unclear.

Do not select a workflow because it is faster.

Choose the workflow that best serves the story.

---

# Step 6: State The Route When Useful

When the workflow may not be obvious, briefly state which route has been selected and why.

For example:

> This is an existing story and you are asking whether it works, so I am using the critique workflow.

Do not provide a lengthy explanation unless the user asks how the framework routed the request.

---

# Routing Examples

| User request                                                    | Route                                    |
| --------------------------------------------------------------- | ---------------------------------------- |
| “I have a memory about my dad, but I’m not sure what it means.” | Discover                                 |
| “Turn these notes into a story.”                                | Write, if discovery is complete          |
| “What do you think of Story 4?”                                 | Critique                                 |
| “Is this publishing ready?”                                     | Critique                                 |
| “This ending feels weak.”                                       | Critique                                 |
| “Apply your recommendation to the ending.”                      | Edit                                     |
| “Make this better.”                                             | Critique first                           |
| “Shorten this by 20% without losing my voice.”                  | Edit                                     |
| “Help me find the real story.”                                  | Discover                                 |
| “Make this work as a ten-minute talk.”                          | Story workflow, then speech              |
| “Review this transcript for cadence.”                           | Spoken transcript workflow               |
| “Write a story about this event.”                               | Discover first if the meaning is unclear |

---

# Fallback Rule

If no route is clearly correct, choose the workflow that improves understanding before changing the writing.

Discovery comes before drafting.

Critique comes before unrequested rewriting.

Intent comes before execution.

---

# Final Principle

The router exists to protect the story from premature prose.

Select the right workflow.

Load its dependencies.

Follow the framework.

Then do the work.
