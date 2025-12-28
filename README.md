# Amplifier Python LSP Bundle

**Python code intelligence via Pyright Language Server**

The Python LSP Bundle provides pre-configured Python language support for Amplifier's LSP capabilities, enabling semantic code navigation, type information, and intelligent code exploration for Python projects.

## What Is This Bundle?

This bundle extends the core LSP bundle with Python-specific configuration, allowing AI agents to:

- **Navigate Python code** - Jump to definitions, find references, locate implementations
- **Understand types** - Get type information, hover documentation, and call hierarchies
- **Explore modules** - List symbols, search across the workspace
- **Use Pyright** - Pre-configured to use Pyright language server

## Components

This bundle provides:

1. **python-lsp** - Behavior configuring Pyright as the Python language server
2. **python-code-intel** - Agent specialized for Python code exploration
3. **python-lsp** - Context providing Python-specific LSP usage guidance

The bundle includes the core `lsp` bundle, which provides the `tool-lsp` module and general LSP capabilities.

## Prerequisites

Pyright must be installed in your environment:

```bash
# Using npm
npm install -g pyright

# Using pip
pip install pyright
```

## Installation

### Using the Bundle

Load the bundle directly with Amplifier:

```bash
# Load from git URL
amplifier bundle use git+https://github.com/microsoft/amplifier-bundle-lsp-python@main
```

### Including in Another Bundle

Add to your bundle's `includes:` section:

```yaml
includes:
  - bundle: lsp-python
```

## Quick Start

### Basic Usage

```bash
# Start a session with Python LSP capabilities
amplifier run --bundle lsp-python

# Navigate Python code
> Find all references to the Session class
> Go to the definition of async_mount
> What parameters does create_session accept?
> Show me the call hierarchy for the execute method
```

### Example Queries

```bash
# Type information
> What type does get_provider() return?

# Symbol search
> Find all classes that inherit from BaseProvider

# References
> Where is the Config model used in this project?

# Call hierarchy
> What functions call emit_event?
> What does the mount function call?
```

## Configuration

The bundle comes pre-configured for Python with Pyright. The default configuration:

```yaml
tools:
  - module: tool-lsp
    config:
      languages:
        python:
          command: ["pyright-langserver", "--stdio"]
          file_patterns: ["*.py"]
```

### Customizing

Override the configuration in your behavior:

```yaml
tools:
  - module: tool-lsp
    config:
      languages:
        python:
          command: ["pyright-langserver", "--stdio"]
          file_patterns: ["*.py", "*.pyi"]
          initialization_options:
            python:
              analysis:
                typeCheckingMode: "strict"
```

## LSP Operations

All operations from the core LSP bundle are available:

| Operation | Description |
|-----------|-------------|
| `goToDefinition` | Find where a symbol is defined |
| `findReferences` | Find all references to a symbol |
| `hover` | Get documentation and type info |
| `documentSymbol` | List all symbols in a file |
| `workspaceSymbol` | Search for symbols across the workspace |
| `goToImplementation` | Find implementations of protocols/ABCs |
| `prepareCallHierarchy` | Get call hierarchy at a position |
| `incomingCalls` | Find callers of a function |
| `outgoingCalls` | Find functions called by a function |

## Bundle Structure

```
amplifier-bundle-lsp-python/
  bundle.yaml           # Bundle definition, includes lsp
  behaviors/
    python-lsp.yaml     # Pyright configuration
  agents/
    python-code-intel.md  # Python-specialized agent
  context/
    python-lsp.md       # Python LSP usage guidance
```

## Philosophy

The Python LSP Bundle follows Amplifier's core principles:

- **Composable** - Extends the core LSP bundle with Python specifics
- **Pre-configured** - Works out of the box with Pyright
- **Observable** - All operations emit events for logging and debugging
- **Minimal** - Adds only Python-specific configuration

## Project Status

**EXPERIMENTAL EXPLORATION**

This is experimental software shared openly but without support infrastructure. See [SUPPORT.md](SUPPORT.md) for details.

## Contributing

This project welcomes contributions and suggestions. Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

---

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft
trademarks or logos is subject to and must follow
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.
