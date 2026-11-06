# NoLoader

NoLoader is an unofficial community build of [NoRisk Launcher](https://github.com/NoRiskClient/noriskclient-launcher) with an extension framework for adding launcher pages, widgets, navigation items, standalone windows, and integrations.

NoLoader extensions customize the launcher; they do not install Minecraft game mods. The project is not affiliated with or endorsed by NoRisk Client. NoRisk names and marks remain the property of their respective owners.

## Download and install

Get the latest Windows release from the [NoLoader releases page](https://github.com/skbenni/NoLoader/releases/latest). Releases include NoLoader Setup and a prepared launcher archive. Setup verifies the signed release catalog and archive checksum before installing. Existing NoRisk Launcher installations need a one-time migration with NoLoader Setup; see the [installation guide](docs/installation.md) for details.

The Windows launcher's automatic updater uses this repository's signed release feed. The updater and installer signing keys are not included in the source tree.

## Build an extension

Start with the [extension guide](docs/modding/getting-started.md). It walks through building and installing the Hello example. The [documentation index](docs/modding/README.md) links to the manifest, API, permissions, lifecycle, and security references.

Requirements: Node.js 24 and Yarn Classic 1.22.

```sh
yarn install --frozen-lockfile
yarn sdk:hello-mod:build
```

Copy `sdk/hello-mod`, including its generated `dist/` directory, into the folder opened by **NoLoader → Open extensions folder**. Refresh the extension manager and enable it. You do not need Rust or the full launcher source to build an extension.

## Build the launcher

The launcher uses a React/TypeScript frontend and a Rust/Tauri desktop host. A full desktop build also needs the stable Rust toolchain and platform-specific Tauri prerequisites.

```sh
git clone https://github.com/skbenni/NoLoader.git
cd NoLoader
yarn install --frozen-lockfile
yarn tauri dev
```

To create a local production build, run:

```sh
yarn tauri build
```

See [development](docs/development.md), [architecture](docs/architecture.md), and the [release process](docs/releases.md) for more details.

## Extension security

Extensions run when enabled and may make network requests. Some APIs can access files, start processes, or execute code in the launcher webview; grant permissions only to extensions you trust. Read the [security guide](docs/modding/security.md) and [permission reference](docs/modding/permissions.md) before installing extensions.

## License and notices

The repository's launcher source is licensed under [GPL-3.0](LICENSE). Third-party components and assets may have separate terms; see [third-party notices](docs/third-party.md). NoLoader is an unofficial community build and is provided without warranty.

## Contributing

Contributions are welcome. Please review [development instructions](docs/development.md), run the relevant checks, and open a pull request against this repository. For bugs and feature requests, use the [issue tracker](https://github.com/skbenni/NoLoader/issues).
