# Changelog

## 1.0.0 (2026-10-22)


### ⚠ BREAKING CHANGES

* the deploy form needs a workspace name; /deployments pages are replaced by /workspaces and /workspaces/<name>/runs/<id>; the runner wire format changed (run_id, workspace_id, phase), so upgrade server and runners together. Existing deployments are migrated to workspaces named <template>-<id prefix>, each with its history as the first run.
* runners no longer read F2S_BACKEND, F2S_BACKEND_CONFIG_* or F2S_STATE_DIR, and the server requires STATE_STORE when deployments are enabled. State in previously configured runner backends is not migrated.

### Features

* Form2Stack is the Terraform state backend, with a resources page ([a617b93](https://github.com/rudesome/Form2Stack/commit/a617b9379e3504a357d6ae337e3fbeb58f19986a))
* form2stack MVP with runners, module registry and template builder ([31e9e0e](https://github.com/rudesome/Form2Stack/commit/31e9e0e68abb059897a0973b8c530dbcdff70232))
* HCP-style workspaces and runs with plan → confirm → apply ([067a5a4](https://github.com/rudesome/Form2Stack/commit/067a5a4a20b29182ceb19f0113ba1a9a9ea90a61))
* OIDC login with user/admin roles, CSRF protection and destroy ([bf84496](https://github.com/rudesome/Form2Stack/commit/bf844969cd5ec8750cb9e11e7d6ede16c38249c0))
* restyled UI and DEPLOYMENTS_ENABLED / REGISTRY_ENABLED switches ([45bdbb7](https://github.com/rudesome/Form2Stack/commit/45bdbb75db601e1e973836d0f9f5037a2f28d0dd))
* runner pools per workspace identity, team access by IdP group, rename and cancel ([4cd6bbe](https://github.com/rudesome/Form2Stack/commit/4cd6bbe0aa42748b07978a068d79142798ad270f))


### Bug Fixes

* just run works in dev shells opened before STATE_STORE existed ([65bcccb](https://github.com/rudesome/Form2Stack/commit/65bcccbcc20768fe4250c267b1c0a1f3d7ccf3de))
