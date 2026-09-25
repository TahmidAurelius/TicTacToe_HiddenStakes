# Session Export Instructions

## About Session Files

The brief requires:
> "The raw session files your tool writes to disk. Not a summary, not a recap you asked the model to write, not a curated log. The machine-generated record."

## Where Claude Code Stores Sessions

Claude Code (VSCode extension) stores session files locally on your machine:

### Windows
```
%USERPROFILE%\.claude\sessions\
```
Example: `C:\Users\YourUsername\.claude\sessions\`

### macOS
```
~/.claude/sessions/
```

### Linux
```
~/.claude/sessions/
```

## Session File Format

Files are typically named:
- `session-*.jsonl` (JSON Lines format)
- `session-*.json` (JSON format)
- Timestamped or UUID-based names

Each line in JSONL files is a complete JSON object representing one interaction.

## What's in Session Files

Each session file contains:
- **Timestamps** of interactions
- **User messages** (your prompts)
- **Assistant responses** (Claude's replies)
- **Tool calls** (which tools were invoked)
- **Tool results** (what each tool returned)
- **Model used** (which Claude model)
- **Complete conversation history**

## How to Export Sessions

### Step 1: Locate Sessions Directory
Open your terminal and navigate to Claude's session directory:

**Windows (PowerShell)**:
```powershell
explorer $env:USERPROFILE\.claude\sessions\
```

**macOS/Linux**:
```bash
open ~/.claude/sessions/
# or
ls ~/.claude/sessions/
```

### Step 2: Copy Session Files
Copy all `.jsonl` and `.json` files from the sessions directory to:
```
transcript/sessions/
```

### Step 3: Create Sessions Folder (if needed)
```bash
mkdir -p transcript/sessions/
```

### Step 4: Copy Files
```bash
# macOS/Linux
cp ~/.claude/sessions/*.jsonl transcript/sessions/
cp ~/.claude/sessions/*.json transcript/sessions/

# Windows PowerShell
Copy-Item "$env:USERPROFILE\.claude\sessions\*" -Destination "transcript/sessions/"
```

## CLAUDE.md File

If a CLAUDE.md configuration file exists in the `.claude/` directory on your local machine, copy it to the project root:

```bash
# macOS/Linux
cp ~/.claude/CLAUDE.md ./CLAUDE.md

# Windows
Copy-Item "$env:USERPROFILE\.claude\CLAUDE.md" -Destination "."
```

This file would contain:
- Claude Code configuration
- Custom rules or instructions
- Model preferences
- Tool settings

## What To Do With Sensitive Data

**Before committing**:
- Redact any API keys or credentials
- Remove personal information if needed
- Remove paths with usernames if sensitive

Example redaction:
```json
// Before
"path": "/Users/john-smith/Projects/..."

// After
"path": "/Users/[REDACTED]/Projects/..."
```

## Step-by-Step for This Project

1. **Go to**: `C:\Users\[YourUsername]\.claude\sessions\` (Windows)
2. **Copy**: All `.jsonl` and `.json` files
3. **Paste into**: `transcript/sessions/` (create folder if needed)
4. **Check for**: CLAUDE.md in `~/.claude/` root
5. **Copy to project root** if found
6. **Review** files for sensitive data and redact if needed
5. **Commit and push**:
   ```bash
   git add transcript/sessions/
   git add CLAUDE.md (if present)
   git commit -m "Add raw session files and configuration

Session files show complete development process with all tool calls,
prompts, and responses from Claude Code.

Co-Authored-By: Claude Haiku 4.5 <noreply@anthropic.com>"
   git push
   ```

## Why This Matters

The brief states:
> "We review the full record of how the work was produced. This is the part of the submission we spend the most time on."

The raw session files prove:
- How iterative the development was
- What tools were used
- How decisions were made
- The actual conversation flow
- Any false starts or abandoned approaches

## Example Session File Structure

```json
{"type": "message", "role": "user", "content": "...", "timestamp": "2026-09-25T10:30:00Z"}
{"type": "tool_call", "name": "Write", "params": {...}, "timestamp": "2026-09-25T10:30:05Z"}
{"type": "tool_result", "name": "Write", "result": "...", "timestamp": "2026-09-25T10:30:06Z"}
{"type": "message", "role": "assistant", "content": "...", "timestamp": "2026-09-25T10:30:10Z"}
...
```

## After Exporting

Once files are added to `transcript/sessions/`:
- They become part of the git history
- Evaluators can see the complete development process
- The transcript is authentic and verifiable
- The submission is complete per brief requirements

---

**Note**: If you don't have `.claude/sessions/` directory, it may mean:
- Claude Code hasn't saved sessions yet in this location
- Sessions may be stored elsewhere on your system
- Check Claude Code settings for session storage location
- Contact Claude Code support for details on your installation
