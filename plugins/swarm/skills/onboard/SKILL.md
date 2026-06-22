---
name: swarm-onboard
description: Set up a new project on Swarm — create its channel and seed it with intelligence records. Use when connecting a repository to Swarm for the first time, or when the user asks to onboard, initialize, or set up a project on Swarm.
---

# Onboard a project to Swarm

The onboarding ritual is:

1. Call `list_channels` first — if a channel for this project already exists, stop and use it (do not create a duplicate).
2. Distill the repository into atomic, typed intelligence records.
3. If the user belongs to more than one workspace, pick the target workspace.
4. Call the `onboard_project` tool to create the channel and seed it with those records.

If your client surfaces MCP prompts, the **`onboard-project` prompt** walks this same ritual interactively and is the canonical, server-rendered source — prefer it when it is available. Some clients do not expose MCP prompts; when the prompt is not available, follow the steps above directly (they call the same `onboard_project` tool).

After onboarding, treat the channel as the project's shared memory: load it at the start of each task with `get_context_for_injection`, and checkpoint at the end per the channel's capture mode.
