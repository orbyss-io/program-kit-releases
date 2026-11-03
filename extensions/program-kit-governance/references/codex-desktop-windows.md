# Program Kit setup boundary for Codex on Windows

Follow the [current installation instructions](https://github.com/orbyss-io/program-kit-releases/blob/main/docs/installation.md)
for the supported initializer and setup sequence.

An authorized agent may initialize Git/Spec Kit and install/update project-local Program Kit files
using existing device tools. Missing or mismatched device/global tools require the human to run
the matching preparation script in their own terminal. Project setup starts no coding worker.

Preserve authored work, Git history and the existing owner's access. A Windows sandbox identity
can cause ownership/DACL failures in generated `.agents`/`.specify` paths. Diagnose actual access
failures and obtain scoped owner repair; rerunning init is not that repair. Do not impose a blanket
human-terminal installation requirement or preemptively change ACLs. Never copy credentials, grant
unrestricted access or loosen the sandbox to hide ownership problems. Interactive launcher startup
and provider account/authority initialization remain human-owned.

After installation use `$speckit-program-kit-governance-product-intake` in the existing Codex
conversation. It supports rough ideas and developed designs, resumable product discovery, connected
founding artifacts, explicit constitution/ADR review and direct first feature intake. The focused
validators check actual content and qualified selections. No nested coding worker or outer workflow
is involved. See [focused product founding](product-founding.md).

The bootstrap workflow is retired. Newly upgraded run/resume/reopen helpers refuse and point to
product-intake. Saved workflow/proof bytes, accepted artifacts and consumer locks remain historical
evidence. Incomplete old runs stay incomplete; do not restart or convert a consumer automatically.

The initializer still owns interpreter checks, catalog registration and toolkit installation. Use
its exact selected Python for the schema dependency when a focused validator requires it. Runtime,
provider, restore and native toolchain checks remain due at the action that uses them; founding
status makes no compatibility claim.
