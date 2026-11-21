<p align="center">
  <a href="https://discountrunners.io">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="assets/wordmark-on-dark.svg">
      <img src="assets/wordmark.svg" alt="DiscountRunners.io" width="420">
    </picture>
  </a>
</p>

<p align="center">
  <strong>Faster, cheaper GitHub Actions runners, and the skills to move your CI onto them.</strong>
</p>

<p align="center">
  <a href="https://discountrunners.io/docs">Docs</a> ·
  <a href="https://discountrunners.io/pricing">Pricing</a> ·
  <a href="https://discountrunners.io/security">Security</a> ·
  <a href="https://discountrunners.io/privacy">Privacy</a>
</p>

---

This plugin connects your coding agent to [DiscountRunners.io](https://discountrunners.io). It
adds our MCP server and a set of skills that read your account's Actions history, find where
your CI is slow or overspending, and open the pull requests that fix it, with your own GitHub
rights.

## Install

```
/plugin marketplace add Discount-Runners-io/plugin
/plugin install discountrunners@discountrunners
```

The first tool call opens your browser to connect your DiscountRunners.io account. Skills are
then available as `/discountrunners:<skill>`, for example `/discountrunners:analyze-my-ci`.

To get new skills as they ship, turn on auto-update for the `discountrunners` marketplace under
`/plugin` → Marketplaces.

## Skills

| Skill | What it does |
|---|---|
| **analyze-my-ci** | Summarizes the last 7 days (or as many as you ask) of a repository's or the whole account's runs: success rate, minutes, spend and savings, and the slowest and most often failing jobs. |
| **optimize-my-ci** | Moves one repository's jobs onto DiscountRunners.io, right-sizes them, finds where workflows could run in parallel, and can test a warm pool. |
| **optimize-all-my-runners** | Ranks the savings across every repository on the account and applies them one pull request at a time. |
| **diagnose-a-job** | Explains why a run was slow or a job waited, failed over or failed, with the run's jobs and steps on one timeline and the failed step's log. |
| **bake-a-runner-image** | Writes an image recipe for the packages jobs install on every run, points the jobs at it and opens the pull request. |
| **cache-docker-builds** | Keeps Docker images, layers and the build cache between runs, on a sticky disk or in the Actions cache, and opens the pull request. |

In apps that show MCP Apps views, answers come with an interactive timeline, log viewer,
parallel plan or summary. Everywhere else the same answers come back as text.

## Permissions

When you connect, you choose what the connection may do:

- **Read** (always on): runner classes, prices, and your account's runs, jobs, steps and logs.
- **Allow changes**: turn warm pools and monitors on and off.
- **Re-run**: re-run a finished run's failed jobs. Our GitHub App starts the re-run on GitHub.

Only the account itself or one of its organization's admins can connect. You can revoke a
connection at any time under Settings → App connections.

## What goes where

The MCP server at `https://mcp.discountrunners.io/mcp` reads the Actions history our GitHub App
imports for your account. Every workflow, variable and pull request change is made with your
own GitHub rights, and the skills ask you before using a right you haven't granted.

Only `runs-on` values, labels, and variable names and values go from your machine to our
server. Workflow files and code stay on your machine. Each variable a skill changes is recorded,
with its old value, in your account's audit log on the Settings page, because variables have no
git history.

## Support

Questions and problems: [discountrunners.io/support](https://discountrunners.io/support).
Security reports: see [SECURITY.md](SECURITY.md).

## License

[MIT](LICENSE) © DiscountRunners.io
