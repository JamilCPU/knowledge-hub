# Knowledge Hub

A planned automated content pipeline for a short-form video channel covering daily AI news and AI learning topics. The pipeline would research stories across several sources, write a script, generate a voiceover, assemble a video under 60 seconds in portrait format, and queue it for approval before posting to TikTok, with other platforms as later phases.

## Status

Design stage only. This repository contains the requirements document (`requirements.md`) and no code. No part of the pipeline has been implemented.

## Planned stack

Taken from the requirements, not yet built:

- Claude for research and script generation
- ElevenLabs for voiceover
- A video assembly tool, still to be chosen (for example FFmpeg)
- A folder-based approval flow: `unapproved/`, `approved/`, `uploaded/`

## Project layout

```
requirements.md   goals, functional requirements, scope, open questions
```
