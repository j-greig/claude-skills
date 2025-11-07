# Claude Skills

Custom Claude Code skills for AI-assisted development workflows.

## What's This?

This repo contains two custom skills for [Claude Code](https://www.anthropic.com/claude/code):

- **context-setter** - Generate comprehensive context-setting markdown files for coding tasks
- **web-browser** - Remote control Chrome/Chromium via CDP for web automation

## Skills

### context-setter

Transforms vague requests into structured, comprehensive prompts for coding tasks.

**Why this matters:** Spending 5-10 minutes building proper context upfront is a worthwhile investment. A well-structured prompt with locked constraints, ordered file reading, and clear deliverables dramatically improves task completion quality and reduces iteration cycles. Context building is task planning.

Creates context files with:

- ROLE definition (who you are for this task)
- MISSION (what you're building/fixing and why)
- CONSTRAINTS (locked decisions sourced from existing docs)
- STYLE (communication preferences, British English by default)
- ORDER OF FILES (absolute paths to read in sequence)
- TASKS (numbered, sequential, with clear deliverables)
- OUTPUT FORMAT (verbosity/format expectations)

**Use proactively** when user intent suggests a complex dev task is beginning.

Example output: `cloudflare-mailbox-mcp-handshake.md`, `pubstack-core-system-build.md`

[Full documentation →](skills/context-setter/SKILL.md)

### web-browser

Minimal CDP tooling for collaborative site exploration. Remote control Chrome/Chromium via DevTools Protocol.

**Tools:**
- `start.js` - Launch Chrome with remote debugging
- `nav.js` - Navigate to URLs
- `eval.js` - Execute JavaScript in active tab
- `screenshot.js` - Capture viewport screenshots
- `pick.js` - Interactive element picker

[Full documentation →](skills/web-browser/SKILL.md)

## Installation

### Option 1: Clone to Claude Code Skills Directory

```bash
# Clone this repo
git clone https://github.com/j-greig/claude-skills.git

# Copy skills to your Claude Code directory
cp -r claude-skills/skills ~/.claude/skills/
```

### Option 2: Symlink (keeps skills up to date)

```bash
# Clone this repo
git clone https://github.com/j-greig/claude-skills.git

# Symlink individual skills
ln -s $(pwd)/claude-skills/skills/context-setter ~/.claude/skills/context-setter
ln -s $(pwd)/claude-skills/skills/web-browser ~/.claude/skills/web-browser
```

## Usage

Skills appear automatically in Claude Code once installed. Claude will invoke them proactively when relevant to the task.

### Manual Invocation

You can also explicitly request a skill:

```
Use the context-setter skill to structure this task
```

```
Use web-browser skill to check this page
```

## Configuration

### context-setter

Edit the default save location in `skills/context-setter/SKILL.md`:

```markdown
**Save Location:**
`/Users/james/Repos/wibandwob-mailbox/workings/context-setting/`
```

Change to your preferred project directory.

### web-browser

Ensure Chrome/Chromium is installed and accessible. Tools expect Chrome running on `:9222` with remote debugging enabled.

## License

MIT

## Credits

- **context-setter** - Original work
- **web-browser** - Adapted from Mario's CDP toolkit

## Contributing

Contributions welcome. Open an issue or PR.

## Links

- [Claude Code Documentation](https://docs.claude.com/en/docs/claude-code)
- [Chrome DevTools Protocol](https://chromedevtools.github.io/devtools-protocol/)
