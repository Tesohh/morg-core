# things we need to decide in meeting / proposals
## repository split proposal (tesohh)
- `morg-core`: the parser, library, cli, lsp
- `morg-server`: the web editor, MCP, ical/ics
- `morg-nvim`: 
## sloppability proposal (tesohh)
- define _read only mode_: 
    - cannot write code, but can help with debugging, brainstorming, understanding code
- `morg-core`: _read only mode_
    - might expand in future to allow only writing boring adaptations (eg. cli, lsp)
- `morg-server`: the web editor is sloppable, the rest is _read only_
- `morg-nvim`: 100% sloppable, MUST follow style guidelines for docs.
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
