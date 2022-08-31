Shinylive Python package
========================

[![Build and test](https://github.com/rstudio/py-shinylive/actions/workflows/build.yml/badge.svg)](https://github.com/rstudio/py-shinylive/actions/)
[![PyPI Latest Release](https://img.shields.io/pypi/v/shinylive.svg)](https://pypi.org/project/shinylive/)

[Documentation site](https://shiny.rstudio.com/py/docs/shinylive.html)

This repository contains a Python package for deploying Shinylive applications.

This repository is not the same as the https://github.com/rstudio/shinylive repository. That repository is used to generate the Shinylive assets distribution, which is a bundle containing HTML, JavaScript, CSS, and wasm files. The Python package in this repository downloads the assets and uses them to create Shinylive application deployments.

## Installation

```
pip install shinylive
```


## Usage

(Optional) Create a basic shiny application in a new directory `myapp/`:

```
shiny create myapp
```

Once you have a Shiny application in `myapp/` and would like create a deployment in `site/`:

```
shinylive deploy myapp site
```

Then you can preview the application by running a web server and visiting it in a browser:

```
python3 -m http.server --directory site 8008
```

At this point, you can deploy the `site/` directory to any static web hosting service.


### Multiple applications

If you have multiple applications that you want to put on the same site, you can deploy them in subdirectories of the site, so that they can all share the same Shinylive assets. You can do this with the `--subdir` option:

```bash
shinylive deploy myapp1 site --subdir app1
shinylive deploy myapp2 site --subdir app2
```


## Shinylive asset management

Each version of the Shinylive Python package is associated with a particular version of the Shinylive web assets. ([See the releases here](https://github.com/rstudio/shinylive/releases).)

To see which version of this Python package you have, and which version of the web assets it is associated with, simply run `shinylive` at the command prompt:

```
$ shinylive
Usage: shinylive [OPTIONS] COMMAND [ARGS]...

  shinylive Python package version: 0.0.1
  shinylive web assets version:     0.0.6
...
```

The web assets will be downloaded and cached the first time you run `shinylive deploy`. Or, you can run `shinylive assets download` to fetch them.

```
$ shinylive assets download
Downloading https://github.com/rstudio/shinylive/releases/download/v0.0.6/shinylive-0.0.6.tar.gz...
Unzipping to /Users/username/Library/Caches/shinylive/
```

To see what versions you have installed, run `shinylive assets info`:

```
$ shinylive assets info
    Local cached shinylive asset dir:
    /Users/username/Library/Caches/shinylive

    Installed versions:
    /Users/username/Library/Caches/shinylive/shinylive-0.0.6
    /Users/username/Library/Caches/shinylive/shinylive-0.0.5
```

You can remove old versions with `shinylive assets remove`. This will remove all versions except the one that the Python package wants to use:

```
$ shinylive assets remove
Keeping version 0.0.6
Removing /Users/username/Library/Caches/shinylive/shinylive-0.0.5
```

If you want to force it to remove the current version, use the `--version` option:

```
$ shinylive assets remove --version 0.0.6
Removing /Users/username/Library/Caches/shinylive/shinylive-0.0.6
```
