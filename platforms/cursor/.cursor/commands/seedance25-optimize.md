Use the project rule `seedance25-prompt-optimizer` to optimize the user's current video idea into a production-ready Seedance 2.5 prompt.

Requirements:
- Preserve all explicit user constraints.
- Infer only low-risk, video-relevant details.
- Route multi-reference, long-video, edit, extend, keyframe, storyboard, blockout, auto-movie, and transition tasks to the matching structure.
- Convert abstract emotion and camera intent into observable, executable instructions.
- Return the final copy-ready prompt first; do not expose hidden reasoning or internal checklists.

If the user has not supplied a video idea yet, ask for one concise input instead of inventing a project.
