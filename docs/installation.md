# Download and install

Choose a version from [Program Kit releases](https://github.com/orbyss-io/program-kit-releases/releases).
Read its release notes and `COMPATIBILITY-<version>.md`. Previews must be chosen
explicitly; they are not an automatic upgrade from a stable version.

## Prepare your machine

Use an existing supported Python (3.11 or newer), Git and Spec Kit (>=1.1.1,<2).
The release's initializer checks those requirements. Prepare missing device tools
in your own terminal using the remediation it prints. An agent must not install
or replace your global tools. A separately selected Python also needs the declared
`packaging>=23` and `PyYAML>=6,<7` libraries. Product-specific .NET, Node, Docker or
other tools are selected and checked when that product needs them.

Create or choose a project directory, initialize Git, and download the initializer
asset matching your operating system and chosen version. Inspect it before running.
The release includes `SHA256SUMS` for verifying downloaded asset bytes.

For example, for the explicitly selected `1.0.0-preview.1`:

```powershell
git init
Invoke-WebRequest https://github.com/orbyss-io/program-kit-releases/releases/download/v1.0.0-preview.1/Initialize-ProgramKit-1.0.0-preview.1.cmd -OutFile Initialize-ProgramKit.cmd
.\Initialize-ProgramKit.cmd codex
```

```bash
git init
curl --fail --location https://github.com/orbyss-io/program-kit-releases/releases/download/v1.0.0-preview.1/Initialize-ProgramKit-1.0.0-preview.1.sh --output Initialize-ProgramKit.sh
bash Initialize-ProgramKit.sh codex
```

Replace `codex` with your supported Spec Kit integration if needed. Public installation
does not need GitHub access to the private source repository. Do not clone that
repository or try to authenticate to it as an installation step.

## What installation does

The initializer checks the selected device tools before changing the project,
initializes Spec Kit with the Python script flavor, registers exact-version public
catalogs, and installs the pinned Program Kit bundle. The bundle contains the
governance, building-block and .NET extensions and the governance preset. Schema
support is set up locally. No coding worker starts during installation.

Keep diagnostics if initialization stops. Fix the reported prerequisite and use
the documented recovery or update route; do not blindly rerun the initializer over
a partial installation. Existing Program Kit installations use the update guidance.

After success, follow [first project and everyday use](usage.md).
