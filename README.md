# VARWG Documentation

Documentation for **VARWG** (Vector Autoregressive Weather Generator), a single-site weather generator developed for hydrodynamic and ecological modelling of lakes.

## Overview

VARWG is a stochastic weather generator that simulates realistic weather sequences while preserving correlations between variables. It supports climate scenario definition, allowing changes to mean values and variability of meteorological variables such as air temperature, which then propagate through to other simulated variables.

This repository contains the **Sphinx-based documentation** for the VARWG library. The documentation is automatically built and hosted on [ReadTheDocs](https://vg-doc.readthedocs.io).

## Project Structure

```
docs/
   source/
      conf.py              # Sphinx configuration
      index.rst            # Main documentation entry point
      reference.rst        # API reference index
      tutorial/            # User guides and tutorials
      generated/           # Auto-generated API documentation
      ...
   Makefile                 # Build targets (html, doctest, linkcheck, etc.)
   _build/                  # Build output directory
src/vg_doc/                  # Package stub
pyproject.toml               # Project metadata and dependencies
```

## Quick Start

### Prerequisites

- Python 3.13+
- [uv](https://docs.astral.sh/uv/) (dependency manager)

### Installation & Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/iskur/varwg-doc.git
   cd varwg-doc
   ```

2. Install dependencies:
   ```bash
   uv sync --dev
   ```

   This installs all project dependencies including Sphinx, matplotlib, IPython, and cartopy.

### Building Documentation

Build HTML documentation locally:

```bash
cd docs
make html
```

The built documentation will be available in `docs/_build/html/`. Open `docs/_build/html/index.html` in your browser to view it.

### Other Build Targets

```bash
cd docs

# Run embedded doctests
make doctest

# Check external links
make linkcheck

# Clean build artifacts
make clean

# Generate PDF (requires LaTeX)
make latexpdf
```

## Documentation Architecture

The documentation is organized into three main sections:

### 1. **Tutorial** (`tutorial/index.rst`)
Getting started guides and how-to documentation for users new to VARWG.

### 2. **API Reference** (`reference.rst`)
Comprehensive API documentation for VARWG modules:
- `varwg.core` - Main weather generator algorithms
- `varwg.meteo.meteox2y` - Meteorological conversion functions (altitude, dewpoint, radiation, etc.)
- `varwg.time_series_analysis.models` - Statistical analysis tools (VAR, VAREX models, model selection)
- `varwg.times` - Time conversion and manipulation utilities
- `varwg.smoothing` - Smoothing and statistical operations

### 3. **Generated API Docs** (`generated/`)
Auto-generated documentation for individual functions, created from docstrings in the [VARWG package](https://github.com/iskur/varwg).

## Key Technologies

- **[Sphinx](https://www.sphinx-doc.org/)** - Documentation generator
- **[NumPyDoc](https://numpydoc.readthedocs.io/)** - NumPy-style docstring parser
- **[Matplotlib](https://matplotlib.org/)** - Plot directives for embedded visualizations
- **[IPython](https://ipython.org/)** - Code highlighting and interactive directives
- **[Cartopy](https://scitools.org.uk/cartopy/)** - Cartographic plotting (tutorials/examples)
- **[ReStructuredText](https://docutils.sourceforge.io/rst.html)** - Documentation markup language

## Development Workflow

### Adding Documentation

1. Create or edit `.rst` files in `docs/source/`
2. Update the appropriate `toctree` directive in index files to include new pages
3. Run `make html` to rebuild and preview locally
4. Use `make doctest` to verify embedded code examples work correctly

### Code Style & Standards

- Follow [NumPy docstring conventions](https://numpydoc.readthedocs.io/en/latest/format.html) for API documentation
- Use reStructuredText format with proper cross-references (`:mod:`, `:func:`, `:class:`)
- Keep documentation in sync with the [VARWG package](https://github.com/iskur/varwg)
- Test all code examples with `make doctest`

### Testing Documentation

```bash
cd docs

# Run doctests to verify code examples
make doctest

# Check for broken links
make linkcheck

# Lint reStructuredText files
restructuredtext-lint source/**/*.rst
```

## Dependency Management

The project uses **uv** for reproducible dependency management:

```bash
# Sync dependencies (install from lock file)
uv sync --dev

# Update lock file after modifying pyproject.toml
uv lock

# Export dependencies for ReadTheDocs
uv export --no-hashes --format requirements.txt > docs/requirements.txt
```

## ReadTheDocs Configuration

The project is configured for automatic builds on ReadTheDocs via `.readthedocs.yaml`:

- Python 3.13 environment
- Builds from `docs/source/conf.py`
- Dependencies installed from `docs/requirements.txt`
- Output directory: `docs/_build/`

## Links & Resources

- **[VARWG Package](https://github.com/iskur/varwg)** - Main source code repository
- **[ReadTheDocs](https://varwg-doc.readthedocs.io)** - Online documentation
- **[Sphinx Documentation](https://www.sphinx-doc.org/)** - Build system reference
- **[ReStructuredText Guide](https://docutils.sourceforge.io/rst.html)** - Markup reference

## Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch
3. Make your changes and test locally with `make html` and `make doctest`
4. Commit with clear messages
5. Open a pull request against the `main` branch

## Project Metadata

- **Name:** varwg-doc
- **Version:** 0.1.0
- **Author:** iskur
- **Python:** 3.13+
- **License:** See LICENSE file (if present)

## Support

For issues, questions, or feature requests:
- Open an issue on the [GitHub repository](https://github.com/iskur/varwg-doc)
- Check the [VARWG package repository](https://github.com/iskur/varwg) for package-specific questions

---

Last updated: 2025-10-22
