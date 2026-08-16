# Dependency Cooldown (Supply Chain)

- A 7-day minimum release age is enforced machine-wide: `~/.npmrc` (`min-release-age=7`, npm >= 11.10), `~/.bunfig.toml`
  (`[install] minimumReleaseAge = 604800`), `~/.yarnrc.yml` (`npmMinimalAgeGate: 10080`), `~/.config/uv/uv.toml`
  (`exclude-newer = "7 days"`). Managed in the chezmoi dotfiles.
- Treat "no matching version" / silently-older resolutions for recent releases as the cooldown working, not a bug: use
  the newest version older than 7 days, or wait. NEVER bypass it — no `--force`, exclusion lists, registry overrides,
  CLI flags, or hand-edited lockfiles — without my explicit approval in the conversation.
- When scaffolding a new project of mine, or adding CI that runs installs, replicate the setting into the repo
  (`bunfig.toml`, `.npmrc`, `.yarnrc.yml`, `pnpm-workspace.yaml` `minimumReleaseAge: 10080`, or `pyproject.toml`
  `[tool.uv] exclude-newer`), since global config does not follow the repo to CI or other machines.
- When adding or editing Renovate/Dependabot config, include the cooldown: Renovate `"minimumReleaseAge": "7 days"`,
  Dependabot `cooldown: { default-days: 7 }`. Security updates may bypass it.
- Cargo and Go have no client-side gate yet: never run blanket `cargo update` / `go get -u`; update crates/modules
  individually (`cargo update <crate> --precise <ver>`) after checking the release is at least 7 days old.
