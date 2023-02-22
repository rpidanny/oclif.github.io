---
title: Plugin Loading
---

Below is a diagram that outlines how a plugin is loaded into the CLI.

There are a couple of important takeaways from this diagram:

### Plugin Resolution Order

Plugins are resolved in the following order:
1. User plugins (i.e. plugins installed by the users)
2. Dev plugins (i.e. plugins listed under `devPlugins`)
3. Core plugins (i.e. plugins listed under `plugins`)

### Manifests Improve Performance

When loading a plugin, oclif needs to require each command file in order to get the static properties of the command - the `description`, `examples`, `flags`, etc...

However, oclif can skip this step if the plugin has an `oclif.manifest.json` (generated by `oclif manifest`). The manifest caches all of these properties so that there's no need to require every single command on every command execution.

## Plugin Loading Diagram

![plugin loading](/img/plugin-loading.jpg)