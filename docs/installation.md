# Download and install

Choose a version from [Program Kit releases](https://github.com/orbyss-io/program-kit-releases/releases).
Read its release notes and `COMPATIBILITY-<version>.md`. Previews must be chosen
explicitly; they are not an automatic upgrade from a stable version.

## Prepare your machine

Use an existing supported Python (3.11 or newer), Git and Spec Kit (>=1.1.1,<2).
The Python selected by the initializer also needs `packaging>=23` and
`PyYAML>=6,<7`. Check the default Python in your terminal:

```text
python -c "import sys, packaging, yaml; print(sys.executable); print('packaging:', packaging.__version__, 'PyYAML:', yaml.__version__)"
```

If either library is missing or outside the supported range, prepare it in that
Python in your own terminal, or select an existing Python that already has both.
For example, to prepare the default Python yourself:

```text
python -m pip install "packaging>=23" "PyYAML>=6,<7"
```

To select another existing Python for this terminal, set `SPECKIT_PYTHON` to its
absolute executable path before running the initializer. Replace the example path
with your own:

```powershell
$env:SPECKIT_PYTHON = "C:\path\to\python.exe"
```

```bash
export SPECKIT_PYTHON="/path/to/python3"
```

Run the check above with the selected executable in place of `python`. The
initializer checks the selected tools and prints remediation for missing
prerequisites. An agent must not install or replace global device tools.
Product-specific .NET, Node, Docker or other tools are selected and checked when
that product needs them.

Create or choose a project directory, initialize Git, and download the initializer
asset matching your operating system and chosen version. Inspect it before running.
The release includes `SHA256SUMS` for verifying downloaded asset bytes.

For example, for the explicitly selected `1.0.0-preview.3`:

```powershell
git init
Invoke-WebRequest https://github.com/orbyss-io/program-kit-releases/releases/download/v1.0.0-preview.3/Initialize-ProgramKit-1.0.0-preview.3.cmd -OutFile Initialize-ProgramKit.cmd
.\Initialize-ProgramKit.cmd codex
```

```bash
git init
curl --fail --location https://github.com/orbyss-io/program-kit-releases/releases/download/v1.0.0-preview.3/Initialize-ProgramKit-1.0.0-preview.3.sh --output Initialize-ProgramKit.sh
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
