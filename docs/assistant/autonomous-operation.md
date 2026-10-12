# Autonomous Operation Policy

## Purpose

Allow a lifecycle conversation to work independently without depending on another supervising chat.

## Standard Startup

A new conversation SHOULD start from:

`docs/prompts/00-resume.md`

The conversation then discovers the active lifecycle state and loads the correct stage prompt.

## Autonomous Continuation

After startup, continue working until:
- the stage output is complete;
- a real business decision is missing;
- user/CI execution evidence is required;
- a security/privacy boundary blocks further work;
- a source-of-truth conflict requires user resolution.

Do not stop for routine confirmation.

## Required Autonomous Loop

For every substantial scope:

1. LOAD
   - read governing policies;
   - read operational memory;
   - read active lifecycle artifacts;
   - inspect relevant code/tests.

2. UNDERSTAND
   - determine lifecycle stage;
   - determine current REQ/TASK/TEST;
   - determine last verified evidence;
   - identify blockers.

3. EXECUTE
   - perform only the active stage;
   - follow current documentation;
   - follow strict TDD where applicable.

4. SELF-REVIEW
   - verify against higher-priority artifacts;
   - challenge assumptions;
   - search for missing edge cases;
   - search for security/concurrency/UX/testing risks.

5. DELIVER
   - produce stage artifact or code/test patch;
   - explain user actions in `pt-BR`.

6. PERSIST
   - propose updates to operational memory files;
   - propose next handoff.

7. CONTINUE
   - if no blocker exists, proceed to the next permitted action within the same active stage;
   - do not jump lifecycle stages automatically unless the stage's output is complete and the user explicitly initiates/accepts the next stage.

## User Dependency Minimization

Ask the user only for:
- business decisions that cannot be derived;
- missing credentials/environment information required for local action;
- execution evidence required by TDD;
- conflict resolution between authoritative project sources;
- explicit approval when policy requires it.

Do not ask the user to restate repository information that can be read directly.
