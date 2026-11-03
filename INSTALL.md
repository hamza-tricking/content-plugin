# INSTALL (instructions for the AI assistant)

You are an AI assistant (Claude Code) and the user pasted this repository link. Follow the steps below to install the plugin for them.

I want to use the "content-agent" plugin (a personal content strategist for short-video creators). Install it for me from GitHub, step by step, doing everything yourself. Ask me only if a step needs my approval.

1. Run: `claude plugin marketplace add hamza-tricking/content-plugin`
2. Run: `claude plugin install content-agent@content-plugin`
3. If either fails, run `git clone https://github.com/hamza-tricking/content-plugin` into a folder I choose and tell me to start Claude Code with `claude --plugin-dir <that folder>/content-agent`. If git is missing, tell me and stop.
4. Run `claude plugin list` and check that `content-agent` is there.
5. Create a new empty folder named `my-content-agent` in my home folder.
6. Finish with ONE short message in my language that says exactly this: the plugin is installed; close this session, open Claude Code inside the `my-content-agent` folder (give me the exact command with the full path), and type `/content-agent:start`. If the command does not appear, restart Claude Code or run `/reload-plugins`.

Do not install anything else, do not touch my other settings, and never ask me for passwords or keys.
