# things we need to decide in meeting / proposals
## repository split proposal (tesohh)
- `morg-core`: the parser, library, cli, lsp (tesohh)
- `morg-server`: the web editor, MCP, ical/ics (mat)
- `morg-nvim`: neovim plugin (tesohh)
- `morg-obsidian`: obsidina plugin (mat)
agreed
## lsp? (tesohh)
- LSP could be a nice fit for the nvim <-> core communication
- Alternatives:
    - CLI
        - good: simple and reusable by scripts
        - bad: but must launch a new process FOR EACH ACTION
    - stdio server
        - good: fast
        - bad: must define a protocol, pretty much reinventing LSP, must reimplement a lot
- LSP actions feel natural and need no extra editor specific impl
    - gd for following links
    - K for hovering info (eg. hover over a timestamp to see repeat dates, or a calendar render...)
    - Completion
    - more...
- Anything that isn't in LSP standard: custom LSP methods
- Anything that needs custom editor implementation: neovim plugin
agreed
## sloppability proposal (tesohh)
- define _read only mode_: 
    - cannot write code, but can help with debugging, brainstorming, understanding code
- `morg-core`: _read only mode_
    - might expand in future to allow only writing boring adaptations (eg. cli, lsp)
    - Allow for writing unit tests
- `morg-server`: the web editor is sloppable, the rest is _read only_
- `morg-nvim`: 100% sloppable, MUST follow style guidelines for docs.
- `morg-obsidian`: 100% sloppable, MUST follow style guidelines for docs.
agreed
## parser (tesohh)
- choose between:
    - [x] build a Transformer on top of `goldmark` (more reliable, less "fun", more dependency baggage)
    - build a custom parser (more code, less reliable, lighter, no deps)
- we don't need to parse ALL markdown, just the parts that we need, and put the rest in generic `Text` nodes
## alerts (mat)
- add an `urgent` flag to tasks that skips calendar alerts, and uses ntfy.sh
## timestamps (tesohh)
- we need to choose a syntax for timestamp ranges for schedule etc.
- org mode does not support timestamps that range over midnight, but we can
