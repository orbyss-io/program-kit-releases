# Updates and compatibility

Always read the target release's compatibility notes. The 0.x to 1.0 preview
boundary requires a fresh checkout and fresh intake, using existing authored
architecture and product documents as input. Preserve the original project and
its history. Old workflow state is not migrated or relabeled as new acceptance.

For later preview toolkit refreshes, download and verify both the new and the
previous version's `program-kit-tooling-<version>.zip`. Extract each into a separate
directory, then use the new version's updater:

```text
python <new-tooling>/scripts/upgrade_program_kit.py --release-root <new-tooling> --previous-release-root <previous-tooling> --target <project> --plan
python <new-tooling>/scripts/upgrade_program_kit.py --release-root <new-tooling> --previous-release-root <previous-tooling> --target <project>
```

Review the plan first. This refresh preserves authored documents, specifications,
application code and native dependency locks. Customized, unknown or conflicting
toolkit ownership is refused for owner reconciliation. It does not perform an
application dependency upgrade or establish acceptance of your application.

After the source repository becomes private, historical initializer URLs under
`orbyss-io/program-kit` cannot be used anonymously. Use the supported initializer
from `orbyss-io/program-kit-releases`. Historical MIT downloads, if mirrored, retain
their original bytes and terms; an old embedded URL is not silently rewritten.
