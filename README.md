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

## Contributing

> [!NOTE]
> This project is not currently accepting external contributions, but we're actively working toward opening this up. We value community input and look forward to collaborating in the future. For now, feel free to fork and experiment!

Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit [Contributor License Agreements](https://cla.opensource.microsoft.com).

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft
trademarks or logos is subject to and must follow
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.
