# dxon registry

this repo holds templates for [**dxon**](https://github.com/P8labs/dxon).

nothing complicated here. it's just a collection of environment templates so people can spin up dev containers quickly.

dxon pulls templates from here when you do something like:

```

dxon create myenv --template node

```

and yeah that's basically the whole idea.


## how it works

templates are just yaml files describing a dev environment.

things like:

- base distro (arch / debian / alpine)
- packages to install
- setup steps
- optional prompts

dxon downloads the template and runs it while creating the container.

templates follow the schema:

```

schema: dxon/v1

```


## repo structure

pretty simple.

- `templates/` → actual environment templates  
- `registry.json` → index used by the dxon CLI


## example template

example `node.yaml`:

```yaml
schema: dxon/v1

name: node
description: node development container

base: arch

packages:
  arch:
    - nodejs
    - npm

steps:
  - run: corepack enable
````

nothing fancy.


## using templates

once dxon is configured with this registry you can run:

```
dxon create project --template nodejs
```

or use the raw template:

```
dxon create mw1 --template https://raw.githubusercontent.com/P8labs/dxon-registry/master/templates/nodejs.yaml
```


## adding a template

1. create a file in `templates/`
2. name it `<template>.yaml`
3. add it to `registry.json`
4. open a PR

keep templates simple and general.


## project

this registry is maintained by **P8labs Team**
part of the [dxon](https://github.com/P8labs/dxon) project.


## license

MIT

