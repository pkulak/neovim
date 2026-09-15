# Neovim

My personal Neovim configuration, packaged as a standalone Nix flake using [`nix-wrapper-modules`](https://github.com/BirdeeHub/nix-wrapper-modules).

## Run directly

```bash
nix run github:pkulak/neovim
```

## Flake usage

Add to your `flake.nix` inputs:

```nix
{
  inputs = {
    nixpkgs.url = "github:NixOS/nixpkgs/nixos-unstable";
    neovim = {
      url = "github:pkulak/neovim";
      inputs.nixpkgs.follows = "nixpkgs";
    };
  };

  outputs = { self, nixpkgs, neovim, ... }: {
    # Overlay:
    # nixpkgs.overlays = [ neovim.overlays.default ];

    # Or package directly:
    # environment.systemPackages = [ neovim.packages.${system}.default ];
  };
}
```
