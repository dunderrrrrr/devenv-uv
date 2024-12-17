# devenv with uv on nix

This assumes you already have `devenv` installed. If not, [install it](https://devenv.sh/getting-started/).

```shell
$ devenv init
```

Example `devenv.nix` with Python 3.12 and `uv`.

```nix
{
  pkgs,
  lib,
  config,
  inputs,
  ...
}: {
  packages = [
    pkgs.git
    pkgs.alejandra
  ];

  languages = {
    python = {
      enable = true;
      package = pkgs.python312;

      venv.enable = true;

      uv = {
        enable = true;
        sync.enable = true;
      };
    };
  };
}
```

```shell
$ uv init
$ uv add htpy
```

```shell
$ python
>>> import htpy
>>> from htpy import h1
>>> str(h1["hello world"])
Markup('<h1>hello world</h1>')
```
