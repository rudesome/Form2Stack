# Changelog

## 1.0.0 (2026-10-23)


### ⚠ BREAKING CHANGES

* VCS-linked workspaces no longer get global variable sets; an admin must attach the sets they need. New VCS connections let workspaces link no repositories until an admin sets patterns. Existing connections are migrated to allow */*.
* add templates to workspaces, state rollback and outputs per state version
* GET /resources no longer exists.
* runner pools are removed. Templates no longer accept "identities", `form2stack token` and `just token`/`just runner` take no pool argument, and the workspace and token identity columns are dropped. Runs queued for a pool are errored by the migration: move each pool's credentials into a variable set, attach it, and start new runs.
* the deploy form needs a workspace name; /deployments pages are replaced by /workspaces and /workspaces/<name>/runs/<id>; the runner wire format changed (run_id, workspace_id, phase), so upgrade server and runners together. Existing deployments are migrated to workspaces named <template>-<id prefix>, each with its history as the first run.
* runners no longer read F2S_BACKEND, F2S_BACKEND_CONFIG_* or F2S_STATE_DIR, and the server requires STATE_STORE when deployments are enabled. State in previously configured runner backends is not migrated.

### Features

* add settings page to workspace ([2f263e6](https://github.com/rudesome/Form2Stack/commit/2f263e6422c9c90a052342ff0e04dd3651cee93b))
* add templates to workspaces, state rollback and outputs per state version ([bd06be1](https://github.com/rudesome/Form2Stack/commit/bd06be10660ebcf2050ac1d5264c9bdecfca31b9))
* allow workspace deletion and destroy resources when removing the last template ([5159532](https://github.com/rudesome/Form2Stack/commit/51595326972c5bfe2de0bb3ee4a0a155a9026670))
* drop the global resources page; registry shows latest versions; dropdowns for known values ([8890a83](https://github.com/rudesome/Form2Stack/commit/8890a83a6fd71201979faed133feb862d3b2fb4b))
* execution mode per workspace, reworked variables page ([cdcea2f](https://github.com/rudesome/Form2Stack/commit/cdcea2f5b02ad7f1cad3418e14b309e74553a037))
* Form2Stack is the Terraform state backend, with a resources page ([a617b93](https://github.com/rudesome/Form2Stack/commit/a617b9379e3504a357d6ae337e3fbeb58f19986a))
* form2stack MVP with runners, module registry and template builder ([31e9e0e](https://github.com/rudesome/Form2Stack/commit/31e9e0e68abb059897a0973b8c530dbcdff70232))
* harden runners, VCS-linked workspaces and the state store ([fe69061](https://github.com/rudesome/Form2Stack/commit/fe690613110e128a440b2c8b7a9293d34c66ca3e))
* HCP-style workspaces and runs with plan → confirm → apply ([067a5a4](https://github.com/rudesome/Form2Stack/commit/067a5a4a20b29182ceb19f0113ba1a9a9ea90a61))
* OIDC login with user/admin roles, CSRF protection and destroy ([bf84496](https://github.com/rudesome/Form2Stack/commit/bf844969cd5ec8750cb9e11e7d6ede16c38249c0))
* publish registry modules from GitHub and Azure DevOps, with no-code updates ([5f74191](https://github.com/rudesome/Form2Stack/commit/5f741911deb7050166fc493a01eb9ef657709bcf))
* refresh-only and replace runs, drift detection, and a reworked workspace UI ([7161ae9](https://github.com/rudesome/Form2Stack/commit/7161ae9d09431df8005e99301fc27cd59a7aff15))
* restyled UI and DEPLOYMENTS_ENABLED / REGISTRY_ENABLED switches ([45bdbb7](https://github.com/rudesome/Form2Stack/commit/45bdbb75db601e1e973836d0f9f5037a2f28d0dd))
* runner pools per workspace identity, team access by IdP group, rename and cancel ([4cd6bbe](https://github.com/rudesome/Form2Stack/commit/4cd6bbe0aa42748b07978a068d79142798ad270f))
* terraform login, the cloud block and remote state sharing ([40688a8](https://github.com/rudesome/Form2Stack/commit/40688a88fdcd94bea22896a9541fcda4db049516))
* variables and variable sets replace runner pools ([427c41a](https://github.com/rudesome/Form2Stack/commit/427c41acfbc6fdc9ea2341aaa51e315c0bcdc392))
* workspaces without templates: blank, state upload and VCS branches ([dcf8522](https://github.com/rudesome/Form2Stack/commit/dcf8522c6f614463d21f6ab5310f6cd04f292af9))


### Bug Fixes

* delete workspace queue ([9a879b6](https://github.com/rudesome/Form2Stack/commit/9a879b66d4eb6d0c9522396d6c862f28cd867294))
* escape nested runner inputs, warn on an unencrypted state store ([f696846](https://github.com/rudesome/Form2Stack/commit/f696846ca369d52e98af5078fe9060154c23b8c8))
* just run works in dev shells opened before STATE_STORE existed ([65bcccb](https://github.com/rudesome/Form2Stack/commit/65bcccbcc20768fe4250c267b1c0a1f3d7ccf3de))
* patch reachable Go vulnerabilities and decouple releases from CI ([0069fc3](https://github.com/rudesome/Form2Stack/commit/0069fc341a7e710d8d3d4dcaa583ff29d60ec710))
