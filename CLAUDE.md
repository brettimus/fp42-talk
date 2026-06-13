# CLAUDE.md

This repo is a Slidev presentation for the FP42 talk. It is based on the previous Codex talk structure, with local issue tracking handled by fp.

## fp workflow

@FP_CLAUDE.md

### notifications

you have a script you can run (`bun run scripts/poke.ts`) in order to ping me with updates after finishing milestones (no need after every task - just when something big has been achieved, like a draft is done, or updates are ready for review in some capacity, or when you are proud of your work

## Visual Iteration with agent-browser

Use agent-browser to inspect and iterate on slide design visually.

## Expected workflow

This talk is meant to be deployed and checked iteratively. After meaningful slide
or styling changes:

1. Build the deck:
   ```bash
   bun run build
   ```

2. Deploy to the live custom domain:
   ```bash
   direnv exec . bun run deploy
   ```

3. Check the deployed output at `https://fp42.boots.lol` with agent-browser.
   Inspect the actual production URL, not just the local dev server, because
   Cloudflare routing, static assets, and refresh behavior are part of the
   expected presentation surface.

4. Iterate until the deployed slides look correct and navigation works.

Local serving is still useful for fast visual iteration, but a task is not done
until the deployed version has been checked.

### Setup

Use the repo-local `agent-browser` skill. No additional setup required.

### Workflow

1. **Build slides** (required - dev server doesn't stay running in background):
   ```bash
   bun run build
   ```

2. **Serve the built slides**:
   ```bash
   cd dist && python3 -m http.server 3031 &
   ```

3. **Open in agent-browser**:
   ```bash
   agent-browser open http://localhost:3031
   ```

   For final checks, open the deployed URL:
   ```bash
   agent-browser open https://fp42.boots.lol
   ```

4. **Inspect slides**:
   ```bash
   agent-browser snapshot -i          # Get interactive elements with refs
   agent-browser screenshot slide.png # Take screenshot for visual review
   agent-browser click @e3            # Navigate (e3 = next slide button)
   ```

5. **Close when done**:
   ```bash
   agent-browser close
   ```

### Navigation Refs

- `@e1` - Enter fullscreen
- `@e2` - Previous slide
- `@e3` - Next slide
- `@e4` - Show overview
- `@e5` - Toggle dark mode
