# Changelog

[English](#english) | [Português](#português)

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## English

---

## [0.5.2] - 2026-06-25

### Changed

- **Base Module**: Removed WhatsApp and Spotify (now 5 programs instead of 7)
  - Keep only essential programs: Firefox, Git, VLC, WinRAR, LibreOffice
  - Reduces bloat and improves focus on core utilities

- **Admin Privileges Handling**
  - Enhanced `setup.ps1` to ask user if they want to continue without admin
  - Better warning messages about admin requirements
  - Added command examples for running with elevated privileges

### Added

- **New Documentation**: `docs/ADMIN-PRIVILEGES.md`
  - Complete guide on running scripts with administrator privileges
  - 4 methods to elevate: right-click, command line, function, auto-detection
  - Explains PowerShell elevation (equivalent to `sudo`)
  - Troubleshooting guide for UAC and execution policy issues

---

## [0.5.1] - 2026-06-25

### Added

- **Shell Module** - PowerShell enhancement with Oh My Posh
  - Install Oh My Posh for modern, customizable prompt
  - Install Fira Code font with ligature support
  - PSReadLine enhancements: history search, tab completion, prediction
  - Keyboard shortcuts: Ctrl+R, Ctrl+S, Ctrl+A, Ctrl+E, word jump
  - Custom aliases: `ll`, `la`, `grep`, `touch` (bash-like)
  - Windows Terminal integration with Fira Code auto-config
  - Full PowerShell profile setup with git integration
  - 100+ theme support (dracula, nord, powerlevel10k, catppuccin, etc)

- **Updated Core**
  - `setup.ps1` now supports "shell" group parameter
  - `setup.ps1 -Group shell` to run PowerShell enhancement
  - Added shell to default group execution

### Changed

- Enhanced `setup.ps1` to include 7th group (shell) in default run

---

## [0.5.0] - 2026-06-25

### Added

- **Customize Module** - Windows UI and shell customizations
  - File Explorer: Show hidden files, extensions, full path, List view
  - Context Menu: Remove "Share", add Notepad++ option
  - Taskbar: Show all system tray icons, disable widgets, disable Cortana
  - Start Menu: Remove recommendations and suggested apps
  - Visual: Dark mode, remove shortcut arrows
  - Input Devices: Mouse acceleration disable, pointer shadow, keyboard settings
  - 18+ Registry-based UI customizations

- **Updated Core**
  - `setup.ps1` now supports "customize" group parameter
  - `setup.ps1 -Group customize` to run UI customizations
  - Added customize to default group execution

### Changed

- Enhanced `setup.ps1` to include 6th group (customize) in default run

---

## [0.4.0] - 2026-06-24

### Added

- **Optimize Module** - System optimization and privacy tweaks
  - Disable diagnostic data collection and telemetry
  - Disable background application activity
  - Disable App Installer (Push Installation)
  - Disable Find My Device
  - Disable Activity History sync
  - Disable Problem Steps Recorder (PSR)
  - Disable automatic update notifications
  - Disable File Explorer insights
  - Disable Start menu recent documents history
  - Disable Windows Defender SmartScreen
  - Disable settings sync (Accessibility, Apps, Personalization, StartLayout)
  - Disable Cortana
  - Disable automatic driver installation
  - 15+ Registry-based optimizations from Group Policy Editor

- **Updated Core**
  - `setup.ps1` now supports "optimize" group parameter
  - `setup.ps1 -Group optimize` to run optimizations
  - Added optimize to default group execution

### Changed

- Enhanced `setup.ps1` to include 5th group (optimize) in default run

---

## [0.1.0] - 2026-06-22

### Added

- **Core Installation Framework**
  - Main `setup.ps1` entry point with modular group execution
  - Multi-method installation chain: Winget → Chocolatey → Custom URL
  - Automatic Chocolatey installation when needed
  - UAC elevation request for admin privileges

- **Installation Utilities**
  - `Install-Program()` - Main installation function supporting 3 fallback methods
  - `Install-FromUrl()` - Download and execute custom installers
  - `Apply-SystemConfig()` - Apply system configurations with error handling

- **Program Validation (4 detection methods)**
  - `Test-ProgramInstalled()` - Quick installation check
  - `Get-InstallationStatus()` - Detailed detection information
  - `Show-InstallationReport()` - Visual installation reports
  - Executable command search
  - Windows Package Manager (Get-Package) check
  - Winget list verification
  - Windows Registry uninstall key search

- **Logging & Output**
  - `Write-Log()` - Timestamped colored output with 5 severity levels
  - `Write-GroupHeader()` - Format group section headers
  - `Write-Section()` - Generic section headers

- **System Utilities**
  - `Test-IsElevated()` - Check admin privileges
  - `Request-Elevation()` - Automatic UAC elevation
  - `Get-InstalledPrograms()` - List all installed packages
  - `Wait-ProcessExit()` - Wait for process completion

- **Registry Operations**
  - `Set-RegistryValue()` - Set registry entries (auto-creates paths)
  - `Get-RegistryValue()` - Read registry values with defaults
  - `Enable-Feature()` / `Disable-Feature()` - Windows optional features
  - `Set-FileAssociation()` - Configure file type associations

- **Installation Groups** (4 groups, 17 programs)
  - **Base** (7 programs) - Firefox, Git, VLC, WinRAR, LibreOffice, WhatsApp, Spotify
  - **Dev** (4 programs) - VS Code, GitHub Desktop, Claude, Python
  - **Gaming** (2 programs) - Steam, Discord
  - **System** (4 programs) - NVIDIA App, AMD Radeon, CPU-Z, HWMonitor
  - Modular group system for easy customization
  - Winget + Chocolatey fallback for all programs

- **Code Quality**
  - PSScriptAnalyzer integration (`.pslintrc` configuration)
  - `tools/lint.ps1` - Code quality checking script
  - Support for severity filtering and recursive scanning

- **Validation Tools**
  - `tools/validate.ps1` - Installation verification utility
  - Program detection with detailed reporting

- **Documentation**
  - README.md - Getting started guide (bilingual EN/PT-BR)
  - ARCHITECTURE.md - Project design and structure
  - EXAMPLES.md - Configuration examples with all scenarios
  - VALIDATION.md - Installation validation guide
  - LINTING.md - Code quality setup and usage
  - CHOCOLATEY.md - Complete Chocolatey integration guide
  - STRUCTURE.md - Quick file reference
  - CLEANUP.md - Migration guide from old structure

- **Project Structure**
  - `src/core/` - Core business logic
  - `src/utils/` - Reusable utilities (4 files)
  - `src/modules/` - Installation groups (4 files: base, dev, gaming, system)
  - `docs/` - Comprehensive documentation (9 files including GITHUB-ACTIONS.md)
  - `tools/` - Utility scripts (lint, validate)
  - `.github/workflows/` - CI/CD automation (6 workflows)
  - `config/` - Reserved for future configuration
  - `tests/` - Reserved for future testing

### Features

- ✅ Clean separation of concerns (core, utils, modules)
- ✅ Idempotent installation (safe to run multiple times)
- ✅ Automatic program detection with 4 methods
- ✅ Colored logging with timestamps
- ✅ Multi-method fallback installation
- ✅ Professional code quality linting
- ✅ Comprehensive documentation
- ✅ Production-ready architecture
- ✅ Backward compatible design
- ✅ Modular group-based approach

## [Unreleased]

### Planned Features

- [ ] Configuration file format (YAML/JSON)
- [ ] Dry-run mode for preview
- [ ] Rollback functionality
- [ ] Installation parallelization
- [ ] Post-installation verification tests
- [ ] Scoop package manager support
- [ ] Cloud settings synchronization
- [ ] GitHub Actions CI/CD integration
- [ ] Pre-commit hook for code quality

---

## Versioning Strategy

This project follows [Semantic Versioning](https://semver.org/):

- **MAJOR** version (X.0.0) - Breaking changes or major features
- **MINOR** version (0.X.0) - New features (backward compatible)
- **PATCH** version (0.0.X) - Bug fixes and improvements

## Installation Success Rates

| Configuration | Success Rate |
|---|---|
| Winget only | ~70% |
| Winget + Chocolatey | ~95% |
| All 3 methods | ~99% |

## File Statistics

- **Total files**: 20+
- **PowerShell scripts**: 10
- **Documentation files**: 8
- **Configuration files**: 2
- **Total lines of code**: ~1000
- **Documentation lines**: ~2000

---

For more information, see:
- [README.md](README.md) - Getting started
- [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) - Project design
- [docs/EXAMPLES.md](docs/EXAMPLES.md) - Usage examples

---

## Português

### Visão Geral

Registro de todas as alterações notáveis deste projeto.

O formato é baseado em [Keep a Changelog](https://keepachangelog.com/pt-BR/1.0.0/),
e este projeto adere a [Versionamento Semântico](https://semver.org/spec/v2.0.0.html).

### Versão Atual: v0.5.2

#### Recursos Principais

- **15 Programas** organizados em 4 grupos (removidos WhatsApp e Spotify)
- **Otimizações de Sistema** - Módulo com 16+ configurações de privacidade
- **Customizações de UI** - Módulo com 18+ configurações de interface
- **Aprimoramento do Shell** - Oh My Posh + Fira Code + PSReadLine
- **Instalação Multi-método**: Winget → Chocolatey → URL customizada
- **Validação Inteligente**: 4 métodos de detecção de instalação
- **Suporte GPU Dual**: NVIDIA App + AMD Radeon Software
- **6 Workflows GitHub Actions** automáticos
- **Documentação Bilíngue** completa
- **Guia de Admin Privileges**: 4 métodos para elevar privilégios

#### Grupos de Instalação

- **Base (5)**: Firefox, Git, VLC, WinRAR, LibreOffice
- **Dev (4)**: VS Code, GitHub Desktop, Claude, Python
- **Gaming (2)**: Steam, Discord
- **Sistema (4)**: NVIDIA App, AMD Radeon, CPU-Z, HWMonitor
- **Optimize**: Otimizações de privacidade e performance
- **Customize**: Customizações de UI e shell do Windows
- **Shell**: Oh My Posh + Fira Code + PowerShell customization

#### Estatísticas

- **Total de commits**: 46
- **Versões**: 17 (v0.1.0 → v0.5.2)
- **Arquivos**: 26+
- **Scripts PowerShell**: 13
- **Arquivos de documentação**: 11+
- **Linhas de código**: ~1500
- **Linhas de documentação**: ~4000
- **Programas**: 15 (reduzido de 17)

#### Taxa de Sucesso de Instalação

| Configuração | Taxa de Sucesso |
| --- | --- |
| Apenas Winget | ~70% |
| Winget + Chocolatey | ~95% |
| Todos os 3 métodos | ~99% |

#### Mais Informações

- [README.md](README.md) - Como começar
- [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) - Design do projeto
- [docs/EXAMPLES.md](docs/EXAMPLES.md) - Exemplos de uso
- [docs/GITHUB-ACTIONS.md](docs/GITHUB-ACTIONS.md) - Automação CI/CD
