# Program Kit

Program Kit guides product intake and architecture-aware delivery with Spec Kit.
This repository distributes approved releases. Development takes place privately.

Read the [documentation index](docs/README.md), [installation instructions](docs/installation.md),
[usage guide](docs/usage.md), and [AI assistant instructions](docs/ai-assistants.md).
Use the matching release tag for version-specific documentation and previews.

Download an explicitly selected version from [Releases](https://github.com/orbyss-io/program-kit-releases/releases).
In an initialized Git repository, run that release's `Initialize-ProgramKit-<version>.cmd`
(Windows) or `Initialize-ProgramKit-<version>.sh` (Linux/macOS), followed by your
coding assistant integration, for example `codex`. Prepare the device tools in your
own terminal as directed by the initializer; the initializer does not install them.

After installation, start `speckit.program-kit-governance.product-intake` in your
coding assistant. The 1.0 preview requires fresh intake; keep existing authored
work and consult the release's compatibility notes before updating.

## License

Releases carrying the [Program Kit license](LICENSE) allow free personal and
commercial use, including internal modification. Redistribution or resale of
Program Kit itself requires Orbyss's permission. You own your applications; you may
distribute generated application code and adapted application templates under your
own terms. Third-party components retain their own licenses and notices.

Previously distributed MIT versions retain their original license. A public
download does not grant open source rights to a proprietary release.

## Publication

Release assets are built and installation-tested privately, inspected, and approved
through this repository's native GitHub `publication` environment. The public
workflow authorizes the selected candidate; it does not build or check out private
source. Source history and detailed build logs stay in the private repository.

Releases, public repository updates, approval runs and their times remain public.
