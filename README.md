# My Codex Skills Marketplace

This repository contains copies of local skill packages from the user's `.codex/skills` and `.agents/skills` folders. Built-in `.system` skills and marketplace/plugin caches are excluded.

## Import

1. Push this folder to a GitHub repository readable by the destination account.
2. In ChatGPT, open Plugins and choose Add > Add a marketplace (or use the Admin > Plugins flow if the account presents it).
3. Enter the GitHub repository URL and set the path to `.agents/plugins` if the import dialog asks for the manifest directory.
4. Review and install the imported skill plugins.

The catalog includes skill instructions and bundled support files. It does not include chats, billing, local runtime dependencies, connected-app authorizations, or credentials. Skills that depend on Codex-only tools may not work in standard ChatGPT. Gmail and other apps still require separate authorization on the destination account or an approved Composio connection.
