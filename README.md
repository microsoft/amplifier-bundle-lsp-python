# amplifier-bundle-lsp-python

> **DEPRECATED — This bundle has been consolidated into
> [amplifier-bundle-python-dev](https://github.com/microsoft/amplifier-bundle-python-dev).**

This repository is now a **forwarding stub**. It transparently loads `python-dev`
so existing configurations continue to work. A deprecation warning will appear on
session start to guide you through migration.

## Migration

Update your bundle includes:

```diff
- - bundle: git+https://github.com/microsoft/amplifier-bundle-lsp-python@main
+ - bundle: git+https://github.com/microsoft/amplifier-bundle-python-dev@main
```

## What Changed?

The `lsp-python` bundle provided LSP/Pyright support only. The new `python-dev`
bundle includes everything `lsp-python` had, plus:

- **Code quality tools** — ruff formatting/linting and pyright type checking
- **Automatic checking** — hooks that run on file write/edit
- **Expert agent** — `python-dev` agent with full Python development knowledge

## Timeline

This forwarding stub will remain active for 2–3 months to allow migration.
After that, this repository will be archived.

## License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.

This project has adopted the
[Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
