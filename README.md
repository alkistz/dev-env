# Development Environment Setup

A collection of automated installation scripts for setting up a development environment on Linux (specifically optimized for Fedora/RHEL-based distributions).

## Overview

This repository contains a modular setup system that automatically installs and configures various development tools and applications commonly used in software development workflows.

## What's Included

The repository includes installation scripts for:

- **Brave Browser** - Privacy-focused web browser
- **Calibre** - E-book management software
- **GitHub CLI** - Command-line interface for GitHub
- **NordVPN** - VPN client with GUI
- **Poetry** - Python dependency management and packaging tool
- **uv** - Fast Python package installer and resolver
- **Visual Studio Code** - Code editor
- **Zsh with Oh My Zsh** - Enhanced shell with framework

## Project Structure

```
dev-env/
├── README.md          # This documentation
├── run                # Main runner script
└── runs/              # Individual installation scripts
    ├── brave          # Brave browser installation
    ├── calibre        # Calibre e-book manager
    ├── gh_cli         # GitHub CLI installation
    ├── nord_vpn       # NordVPN installation
    ├── poetry         # Poetry installation
    ├── uv             # uv package installer
    ├── vscode         # Visual Studio Code installation
    └── zsh            # Zsh and Oh My Zsh installation
```

## Usage

### Prerequisites

- Linux system (scripts optimized for Fedora/RHEL with `dnf` package manager)
- `bash` shell
- `curl` and `wget` available
- `sudo` privileges for system package installation

### Running All Scripts

To install all available tools:

```bash
./run
```

### Running Specific Scripts

To install only specific tools, use the filter parameter:

```bash
# Install only Poetry
./run poetry

# Install only VS Code
./run vscode

# Install multiple tools (filter matches partial names)
./run vs    # This would match 'vscode'
```

### Dry Run Mode

To see what would be executed without actually running the installations:

```bash
# Dry run for all scripts
./run --dry

# Dry run for specific script
./run --dry poetry
```

## How It Works

1. The main `run` script scans the `runs/` directory for executable scripts
2. It applies any filters you specify to determine which scripts to execute
3. Each script in `runs/` is an independent installation routine for a specific tool
4. Scripts are executed in the order they're found by the file system

## Individual Script Details

### brave

Installs the Brave browser using the official installation script with GPG verification.

### calibre

Installs Calibre e-book management software using the official Linux installer.

### gh_cli

Installs GitHub CLI using DNF5 package manager with the official GitHub repository.

### nord_vpn

Installs NordVPN GUI client using the official installation script.

### poetry

Installs Poetry Python dependency management tool using the official installer.

### uv

Installs uv, a fast Python package installer and resolver, using the official installation script.

### vscode

Installs Visual Studio Code using the official Microsoft repository for RPM-based distributions.

### zsh

Installs Zsh shell via DNF and sets up Oh My Zsh framework for enhanced shell experience.

## Adding New Tools

To add a new tool installation:

1. Create a new executable script in the `runs/` directory
2. Name it after the tool (e.g., `runs/neovim`)
3. Make it executable: `chmod +x runs/neovim`
4. Add your installation commands

Example new script:

```bash
#!/usr/bin/env bash

echo "Installing Neovim"

sudo dnf install neovim -y
```

## Safety Features

- **Dry run mode**: Test what would be executed without making changes
- **Filtering**: Install only the tools you need
- **Independent scripts**: Each tool installation is isolated
- **Logging**: Clear output showing what's being executed

## Troubleshooting

### Permission Issues

If you encounter permission errors, ensure:

- The `run` script is executable: `chmod +x run`
- All scripts in `runs/` are executable: `chmod +x runs/*`
- You have sudo privileges for system installations

### Package Manager Issues

This setup is optimized for Fedora/RHEL systems using `dnf`. For other distributions:

- Debian/Ubuntu: Replace `dnf` with `apt` in relevant scripts
- Arch Linux: Replace `dnf` with `pacman` in relevant scripts

### Network Issues

Most installations require internet connectivity. Ensure you have a stable connection before running the scripts.

## Contributing

To contribute additional tools or improvements:

1. Fork the repository
2. Add your installation script to the `runs/` directory
3. Test thoroughly with `--dry` mode first
4. Submit a pull request with a clear description

## License

This project is provided as-is for educational and development environment setup purposes.
