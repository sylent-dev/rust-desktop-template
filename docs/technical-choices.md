# Technical choices

The technical choices of the [roadmap](../roadmap.md), with their reasons. A project made from the template confirms each one at its start, and records here the choices of its own.

| Topic | Choice | Reason |
|---|---|---|
| Interface | `egui` and `eframe`, with the `glow` renderer (OpenGL) | Immediate mode: the interface is a function of the state, drawn again at each frame, without widgets to keep in sync; one executable on Linux, Windows and macOS, without a web engine. `glow` rather than `wgpu`: a smaller executable and a faster build, enough for a 2D interface. |
| Linux display | X11 always (XWayland under Wayland), chosen in `main.rs` | The same behavior on every Linux desktop: under Wayland, a window can't place itself, nor read the position eframe restores at the next launch. Change it if the application needs Wayland itself (fractional scaling, no XWayland on the desktop). |
| Window title bar | The title bar of the system | The template's default. A project decides in its first wireframes whether it keeps it or draws its own (`with_decorations(false)`, and its buttons from the start). |
| Translations | Fluent (`fluent-bundle`), one `.ftl` file per language in `locales/`, embedded in the executable | Plurals and genders written by the translators, without code. The code names a message by a variant of `Message` or by a method of `Translator` (`src/i18n.rs`), never by a string; a test checks that the code and every file have the same messages. |
| Interface language | The language of the system (`sys-locale`) until the user picks one in the settings | English when the system's language isn't translated. |
| Settings | TOML in the configuration directory of the user (`directories`), written atomically (a new file synced, then renamed); the size and position of the window kept by eframe in `window.ron` next to it | Readable and editable by hand. A value this version can't read takes its default without losing the others; a file that isn't TOML is kept aside (`settings.invalid.toml`) before the defaults replace it. |
| Log | `simplelog` to the standard error | The minimum until the application needs a log file of its own (written in the user's directories, its size bounded). |
| Releases | GitHub Actions workflow triggered by version tags, from a commit of `main` only | Builds every system on its own runner, checks the advisories and the licenses (`cargo-deny`), writes the licenses of the dependencies (`cargo-about`) and publishes the archives with `gh release`, without extra tooling. |
| Rust version | Pinned in `rust-toolchain.toml`, raised by Dependabot | A release is built by the compiler its checks ran with. |
| Actions | Each one pinned to a commit, its version in a comment | A tag can be moved by the owner of the action to another code; `.github/scripts/pinned-actions.sh` fails the CI otherwise. |
| Mock-up server | `python3 docs/mockups/serve.py <port>`, port `<port>` | Serves the mock-up without cache, on a port of its own (choose one between 8700 and 8799, unused by the other projects), so that two projects never take each other's server over. |
