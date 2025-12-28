# Python LSP Context

You have access to Python code intelligence via the LSP tool with Pyright.

## Python-Specific Capabilities

- **Type Information**: Get precise type hints and inferred types
- **Import Resolution**: Trace imports across the project
- **Class Hierarchies**: Navigate inheritance chains
- **Method Resolution Order**: Understand Python MRO
- **Virtual Environments**: Respects pyproject.toml and venv configurations

## Effective Python Navigation

### Finding Class Definitions
1. Position cursor on class name
2. Use `goToDefinition` to find where it's defined
3. Use `findReferences` to see all usages

### Understanding Type Hierarchies
1. Use `hover` on a class to see its bases
2. Use `goToImplementation` to find subclasses
3. Navigate inheritance with repeated `goToDefinition`

### Tracing Function Calls
1. Position on function name
2. Use `incomingCalls` to see what calls this function
3. Use `outgoingCalls` to see what this function calls

## Common Patterns

### Finding Where an Exception is Raised
```
1. hover on ExceptionType to understand it
2. workspaceSymbol to find all definitions
3. findReferences on each to see raise statements
```

### Understanding a Decorator
```
1. goToDefinition on @decorator_name
2. hover to see signature and docstring
3. outgoingCalls to see what it wraps
```

### Navigating Imports
```
1. goToDefinition on imported name
2. Follow chain through __init__.py files
3. documentSymbol to see module structure
```

## Workspace Detection

The Python LSP detects workspace root by looking for:
- pyproject.toml (preferred)
- setup.py
- setup.cfg
- requirements.txt
- .git directory

Ensure your project has one of these at the root for accurate analysis.

## Known Limitations

### Operations Not Fully Supported by Pyright

- **goToImplementation**: Returns empty results. Pyright doesn't support finding subclasses/implementations directly.
  - **Workaround**: Use `findReferences` on the base class and filter for `class` definitions.

- **workspaceSymbol**: May return empty on first use before workspace is indexed.
  - **Workaround**: Run `documentSymbol` on relevant files first to trigger indexing, then retry.

### Type Resolution

- Complex generic types or dynamically-created classes may show as `Unknown`
- Missing stub packages (e.g., `types-requests`) can cause type resolution failures
- Circular imports may confuse type inference
