# Aggy

I write the guides I wish existed, after verifying every line of them. Security hardening for people who run their own servers, local-first AI tooling, and the occasional browser game.

> The rule for everything below: if I haven't spent a ridiculous amount of time thinking about a problem and finding a solution or workaround and an easy way to explain it plainly, with a command you can run to check it, it doesn't ship.

## Things I wish somebody had told me

- **`ssh -V` prints the version. `sshd -T` prints what the daemon offers.** An Amazon Linux 2023 image from August 2026 reports `OpenSSH_9.9p1` and offers no ML-KEM. [How to turn it on and prove it](https://gist.github.com/AUAggy/f1b3c7503e378f0787c51dd8c4fc9473).
- **Reload is not the safe failure.** On RHEL, Fedora, and Amazon Linux, sshd re-executes on SIGHUP with no config check, so a bad file is the same lockout as a restart. `sshd -t` first. [Same guide](https://gist.github.com/AUAggy/f1b3c7503e378f0787c51dd8c4fc9473).
- **An AI agent with a shell can use your SSH keys, your agent, and your open sessions.** "Do not use SSH" in the prompt sets the task. A separate account, a hardware key with touch and PIN, and a read-only brief set the boundary. [The cleanup](https://gist.github.com/AUAggy/c1881c1efd85b6cc46d3564ac9012cf0).
- **"No findings" is not "clean" when the logs are off.** Bedrock model invocation logging is disabled by default, region by region. Until it is on, a prompt-injection incident leaves no audit trail and a scanner can only report "not applicable". [agent-sec-scanners](https://github.com/AUAggy/agent-sec-scanners).
- **CloudTrail records management events by default, and almost nothing you do to data.** Object-level reads of an S3 bucket and every Lambda invocation go unlogged until you turn on data events, which cost extra. [CloudTrail](https://aggyswebservices.com/category/security-identity-compliance/aws-cloudtrail/).
- **The default network ACL allows everything. A custom one denies everything.** Copy the default's rules before you associate a new one, or the subnet goes dark. [VPC](https://aggyswebservices.com/category/networking-content-delivery/amazon-vpc/).
- **S3 has been strongly consistent since December 2020.** Any guide still telling you to design around eventual consistency is describing a service that no longer exists. [S3](https://aggyswebservices.com/category/storage/amazon-s3/).
- **Shield Advanced costs $3,000 a month, plus data transfer fees.** Shield Standard is automatic and free, and it is what most accounts actually have. [Shield](https://aggyswebservices.com/category/security-identity-compliance/aws-shield/).
- **SSH traffic recorded today can be decrypted later.** Harvest now, decrypt later, taught with one worked example and a checklist for your own systems. [HarvestAttack](https://harvestattack.com).
- **Catching a fallacy does not win the argument, and "the AI said so" is an appeal to authority.** A bad argument fails to support a conclusion; it does not disprove it. A model's answer is testimony, not a test. [SpotTheFallacy](https://github.com/AUAggy/SpotTheFallacy).

<details>
<summary>More things I wish somebody had told me</summary>

- **Banned-word lists do not fix AI prose.** "Robust estimator" and "critical section" are terms of art. The slop is padded lead-ins, repeated claims, and canned phrasing. [deslop](https://github.com/AUAggy/deslop).
- **A 3D browser FPS needs no build step, no server, and no telemetry.** One HTML file. Agents wrote the code; I set the constraints and judged what shipped. [Ashworth Station](https://github.com/AUAggy/ashworth-station).
- **The Wednesday row is not about Wednesday.** It is how far through the week you are, and the week starts Monday, so Wednesday lunchtime reads 50%. [Elapsed](https://github.com/AUAggy/elapsed), a clock for where you are in time, not what time it is.

</details>

## What I ship

| Project | What it is | Links |
|---|---|---|
| [agent-sec-scanners](https://github.com/AUAggy/agent-sec-scanners) | AWS Bedrock security auditing as an MCP server and CLI. Findings map to OWASP LLM and Agentic Top 10. | [npm](https://www.npmjs.com/package/@miaggy/mcp-audit) |
| [HarvestAttack](https://github.com/AUAggy/harvestattack) | Harvest now, decrypt later, as a free educational site with one worked example. | [Site](https://harvestattack.com) |
| [AWS in Plain English](https://github.com/AUAggy/aggyswebservices) | 69 AWS services in 12 categories, with plain-language analogies and the gotchas that bite in practice. Scenario figures are labelled illustrative; service facts are kept current. | [Site](https://aggyswebservices.com) |
| [local-llamacpp-pi-guide](https://github.com/AUAggy/local-llamacpp-pi-guide) | Guide and scripts for running Pi with local llama.cpp models on Apple Silicon. Private, zero-cost coding agent with verified tool calling. | - |
| [SpotTheFallacy](https://github.com/AUAggy/SpotTheFallacy) | 120+ scenarios for spotting logical fallacies. | [Site](https://spotthefallacy.com) |
| [markdown-pdf-revived](https://github.com/AUAggy/markdown-pdf-revived) | Privacy-first, offline Markdown to PDF for VS Code, maintained. 12,172 installs across the VS Code Marketplace and Open VSX, November 2026. | [VS Code](https://marketplace.visualstudio.com/items?itemName=AUAggy.markdown-pdf-revived) · [Open VSX](https://open-vsx.org/extension/AUAggy/markdown-pdf-revived) |
| [deslop](https://github.com/AUAggy/deslop) | Rewrites AI-generated prose into clear technical writing. 4,720 installs across the VS Code Marketplace and Open VSX, November 2026. Your model, your key. | [VS Code](https://marketplace.visualstudio.com/items?itemName=AUAggy.deslop) · [Open VSX](https://open-vsx.org/extension/AUAggy/deslop) |
| [supportbot-langchain-demo](https://github.com/AUAggy/supportbot-langchain-demo) | Local RAG agent demo: LangGraph, LangChain tools, FAISS, Streamlit UI. Inspectable tool-calling agents, no OpenAI or Anthropic keys. | - |
| [Ashworth Station](https://github.com/AUAggy/ashworth-station) | A zombie survival FPS in one HTML file. | [Play](https://auaggy.github.io/ashworth-station/) |
| [Elapsed](https://github.com/AUAggy/elapsed) | A dot-matrix clock for the week, month, and year. | [Site](https://auaggy.github.io/elapsed/) |

## How I work

- The AI in my shell is a clanker. It gets its own account, its own key, and a read-only brief.
- Local models first: Pi on a llama.cpp server, Claude Code or Codex through Ollama.
- Facts I can't verify get cut, not hedged.

## Now

The next guide. It gets named here once I can explain it in one sentence and you can check it with one command.

Everything else, including how to reach me: [miaggy.com](https://miaggy.com).
