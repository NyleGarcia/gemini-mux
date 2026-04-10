# claude-mux

A tmux-based multiplexer for [Claude CLI](https://claudecli.com) that allows you to run multiple workstreams in parallel across different git worktrees.

## Features

- **Parallel Workstreams**: Run multiple Claude sessions simultaneously in separate tmux windows.
- **Git Worktree Support**: Each session operates in its own dedicated git worktree, preventing file conflicts during development.
- **Live Status Dashboard**: Real-time monitoring of all active workstreams via the 'status' window.
- **Auto-Notifications**: Get notified when all workstreams have completed their tasks.
- **Automated Integration**: Use the 'combine' command to merge all feature branches into a single integration branch for final verification and testing.
- **Intelligent Resumption**: Automatically resumes the latest session if a worktree already exists, avoiding redundant branch creation.

## Installation

1. Copy the 'claude-mux' script to your $PATH (e.g., '~/scripts/').
2. Ensure you have 'tmux' and 'git' installed.
3. Make the script executable: 'chmod +x claude-mux'.

## Commands

- 'claude-mux start [file] [--yolo]': Start a new session from a configuration file (default: 'WORKSTREAMS.md').
- 'claude-mux add <name> <tree> <task> [--yolo]': Add a single workstream to an active session.
- 'claude-mux status': Display the status of all active workstreams.
- 'claude-mux combine <branch>': Merge all worktree branches into a new integration branch and start a verification session.
- 'claude-mux list': List all windows in the current session.
- 'claude-mux stop': Terminate the tmux session.
- 'claude-mux watch': (Internal) Background watchdog for notifications.

## WORKSTREAMS.md Format

The file uses a colon-separated format:
'name:tree:task'

Example:
```markdown
# WORKSTREAMS.md
auth-fix:feat-auth:Fix the login timeout bug and add unit tests.
ui-update:feat-ui:Implement the new dashboard layout using Vanilla CSS and React.
api-docs:feat-docs:Update the OpenAPI specification for the user profile endpoint.
```

## Contributing

Break your project into parallel tasks, generate your 'WORKSTREAMS.md', and let Claude do the heavy lifting!
