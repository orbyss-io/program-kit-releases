# Native engineering locations

Program Kit supports two maintained layouts, independently of the optional v2
composition model. With no selection, existing default destinations remain in use.
To select the infrastructure boundary, author `config/program-kit/locations.json`:

```json
{ "schemaVersion": 1, "layout": "infra" }
```

The only supported layout names are `default` and `infra`. Unknown fields and
versions fail before reconciliation writes. Do not add location fields to the
composition resource graph; its own schema remains unchanged.

| Owner | Default | Infra |
| --- | --- | --- |
| Maintained Python/PowerShell scripts and sibling schemas | `scripts/` | `infra/tooling/scripts/` |
| Native helper projects and browser tooling | `tools/program-kit/` | `infra/tooling/program-kit/` |
| Local identity imports/themes and profile Compose files | `deploy/` | `infra/docker/` |
| Active v2 Compose output | `artifacts/composition/compose.json` | `infra/docker/compose.json` |
| Mounted host configuration/packages/public content | `artifacts/<runtimeDirectory>/` (or `artifacts/release-bundle/`) | `infra/docker/runtime/<runtimeDirectory>/` (or `runtime/application/`) |
| Common consumer operational scripts | `scripts/` | `infra/scripts/` |

`infra/azure/` is reserved for future consumer-owned assets. Selecting this layout
creates no cloud resources, installs no tools and adds no Azure configuration.
Directories without authored/generated files need not exist yet.

Authoring stays in `config/program-kit/`, including native build policy, selected
profiles, locks/provenance and the managed-file inventory. Root `Directory.*`,
project files, native tool/version selectors and `.github/workflows/` retain their
native entry locations. Root `eng/` remains ignored disposable projections.

## Generate and reconcile

Use the installed `speckit.program-kit-governance.sync` plan/apply operation for
engineering setup. It invokes the existing .NET reconciliation adapter. A full
engineering reconciliation is required to change layouts; `--composition-only`
refuses a changed selection. No additional runner or manual relocation is needed.

Preview the selected layout before applying. The transaction authenticates prior
managed bytes, transfers scaffold customizations, and refuses customized managed
files or conflicting destinations. Existing unowned application scripts/tools are
preserved at their authored locations. Reconcile their call sites through their
consumer owner; Program Kit does not infer or rewrite arbitrary application paths.
Consumer verification may be authored under `infra/scripts/`; legacy root scripts
remain supported during adoption.

Supplier source identities stay distinct from resolved consumer destinations.
Recipes, ownership rows, managed-output hashes, native hooks and workflow commands
are produced together through the existing generator. Never edit consumer hashes
or move individual generated runners to adopt the layout.

## Native commands

For the infra layout:

```powershell
python infra/tooling/scripts/regenerate_eng.py --repository .
./infra/tooling/scripts/Restore.ps1 -Subject Application.slnx -LockedMode
./infra/tooling/scripts/Build.ps1
python infra/tooling/scripts/composition_run.py status
```

Default-layout commands retain their `scripts/` paths. The generator and composition
entrypoint discover the repository from their own installed location when
`--repository` is omitted. PowerShell wrappers locate native `config/program-kit/`
and execute SDK commands from that root, independent of the caller's directory.
Explicit `--repository` paths follow the caller's ordinary path semantics.

Deleting `eng/` and regenerating requires neither Git nor `.specify`/agent metadata.
The existing regeneration command still verifies exact selected helper bytes and
tool/runtime selections. Changed or missing helpers require reconciliation with
the exact selected toolkit. No newer dependency is selected as recovery.

## Preview toolkit adoption

1. Retain the exact previous preview bundle and protect the consumer working tree.
   Stop any running local composition with its current native entrypoint before
   changing its layout. Preserve private storage and prior execution evidence.
2. Preview and apply `upgrade_program_kit.py` using the new toolkit sources and
   `--previous-release-root` with the exact prior sources. This refreshes native
   toolkit components; it does not itself relocate engineering outputs.
3. Author the location selection and use the native sync plan/apply operation for
   the full engineering baseline. Inspect the ownership transfers and conflicts.
   Selected dependency profiles, package versions and locks retain their owners.
4. Regenerate, verify repeated no-drift reconciliation, and execute focused native
   checks. For an existing composition, prepare once through the new entrypoint
   before run/update; old runtime receipts are preserved history, not rewritten.

Local archives used for validation are development artifacts. Their source identity
and hashes do not authorize publication or establish a consumer upgrade. Coordinate
adoption against an explicitly identified bundle after supplier review/merge.
