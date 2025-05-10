# NixOS & Home Manager Setup for Cloud Engineering

This repository contains my personal NixOS and Home Manager configuration, tailored for a cloud engineer. It includes development tools for GCP, AWS, and Azure, as well as common utilities, browsers, and GNOME desktop preferences.

---

## Overview

- System: NixOS 24.05
- Desktop: GNOME (Fedora-like experience)
- Shell: Zsh with Oh My Zsh
- Tools Installed via Home Manager:
  - gcloud, awscli2, azure-cli, terraform
  - firefox, google-chrome
  - neovim, vscode, btop, jq, git, tmux

---

## Home Manager Installation (Non-Flake)

```bash
nix-channel --add https://github.com/nix-community/home-manager/archive/release-24.05.tar.gz home-manager
nix-channel --update
nix-shell '<home-manager>' -A install
```

---

## Applying Configuration

Save your Home Manager config to:

```bash
~/.config/nixpkgs/home.nix
```

Then apply it:

```bash
home-manager switch
```

---

## Rebuilding NixOS

If you make system-level changes in `/etc/nixos/configuration.nix`, apply them with:

```bash
sudo nixos-rebuild switch
```

---

## Maintenance

```bash
nix-collect-garbage -d             # Clean up unused packages and generations
nix-store --gc                     # Free unreferenced paths
home-manager generations           # View Home Manager history
home-manager rollback              # Revert to previous config
```

---

## More Resources

- [NixOS Manual](https://nixos.org/manual/nixos/stable/)
- [Home Manager Docs](https://nix-community.github.io/home-manager/)
- [Nix Pills (Tutorial)](https://nixos.org/guides/nix-pills/)

---

## Notes

- This config is optimized for use in a VM or test environment before full install.
- Switch to flake-based config later for version pinning and reproducibility.

---

## To Do (optional)
- [ ] Integrate Home Manager as a NixOS module
- [ ] Convert to flake structure
- [ ] Add secure secrets management for cloud credentials
