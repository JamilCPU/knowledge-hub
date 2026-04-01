# Requirements: Knowledge Hub

**Status:** Ready for Review
**Last Updated:** 2026-03-23

---

## Goal
Build an AI-automated content channel (Knowledge Hub) that posts short-form educational videos about daily AI news and AI learning topics. The channel launches on TikTok with monetisation as the end goal, and is architected from the start to support expansion to other platforms (YouTube Shorts, Instagram Reels, etc.).

## Users & Stakeholders
- **Channel owner (Jamil):** Reviews and manages the pipeline; primary decision-maker on content direction.
- **Viewers:** People interested in AI — curious generalists, students, tech enthusiasts wanting a daily AI digest.

## Functional Requirements

The system must support a fully automated content pipeline:

1. **Research:** AI scans and retrieves daily AI news from multiple source types in parallel:
   - Social media: X/Twitter, Reddit (e.g. r/artificial, r/MachineLearning, r/technology)
   - Major AI/tech news sites (e.g. The Verge, TechCrunch, Ars Technica, VentureBeat)
   - The system cross-references topics across sources — if a story appears on one site, it seeks out other coverage of the same topic to build a richer, more complete picture before scripting.
   - Goal: produce scripts that are informative and unbiased, not shaped by any single outlet's framing.
2. **Script generation:** AI writes a short-form script based on the researched content, optimised for the target video length.
3. **Voiceover generation:** AI generates an audio voiceover from the script.
4. **Video assembly:** AI assembles a final video combining the voiceover with engaging background footage — real downloaded clips (e.g. Minecraft, GTA driving) or Jamil's own gaming clips — to retain viewer attention through visual stimulation.
5. **Approval workflow:** Videos are managed through a folder-based state system in a designated directory on Jamil's computer:
   - `unapproved/` — all newly generated videos land here by default
   - `approved/` — videos cleared for posting (either manually moved by Jamil, or placed here immediately in fully automated mode)
   - `uploaded/` — videos that have been posted to TikTok, moved here after upload
   - **Manual mode (v1):** video is generated → lands in `unapproved/` → Jamil reviews and moves to `approved/` → gets posted → moved to `uploaded/`
   - **Automated mode (v2):** video is generated → placed directly in `approved/` → gets posted → moved to `uploaded/`
6. **Output:** Finished video file with metadata (title, caption, hashtags) saved alongside the video.

## Non-Functional Requirements
- Pipeline should be capable of producing multiple videos per day.
- Content should feel timely — ideally covering news from the same day or prior 24 hours.

## Scope
### In Scope
- TikTok as the launch platform
- Automated research, scripting, voiceover, and video assembly
- Short-form video format (under 60 seconds)

### Out of Scope (v1)
- Manual video editing
- Live posting/scheduling to TikTok (may be handled separately)
- AI-generated visuals
- Stock footage libraries

### Future Phases (not now)
- Expansion to YouTube Shorts, Instagram Reels, and other platforms
- TikTok monetisation features (once eligibility is reached)

## Constraints
- Keep running costs as low as possible — automation should be efficient, not wasteful
- Claude (already subscribed) for research and scripting
- ElevenLabs for voiceover generation
- No unnecessary paid services — justify each tool before adding it

## Acceptance Criteria
- [ ] v1: Pipeline produces a complete video and surfaces it for Jamil's approval before posting
- [ ] v2: Pipeline can research and produce and post a video with no manual intervention (fully automated mode)
- [ ] Videos are under 60 seconds
- [ ] Multiple videos can be produced in a single day
- [ ] Output includes video file + caption/hashtag metadata ready for posting

## Open Questions

| # | Question | Owner | Status |
|---|----------|-------|--------|
| 1 | Which specific news sites should be on the default source list? (e.g. The Verge, VentureBeat, Ars Technica?) | Jamil | Open |
| 2 | What tool will handle video assembly and trimming clips to match voiceover length? (e.g. FFmpeg, a Python library?) | Jamil | Open |
| 3 | Copyright risk: using downloaded clips for a monetised channel may violate terms of service or copyright law — needs legal consideration before launch. | Jamil | Open |

## Assumptions
- Videos will be portrait orientation (9:16) for TikTok
- English-language content only for v1
- Jamil will handle TikTok account setup and posting manually until automation is confirmed working
- Claude (via Claude Code) handles research and script generation
- ElevenLabs handles voiceover generation
- Video output directory will be `F:\Dev\KnowledgeHub\` with `unapproved\`, `approved\`, and `uploaded\` subfolders — to be created during implementation, not manually
