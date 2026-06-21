# Homebrew tap for Meeting Assistant

Install [Meeting Assistant](https://github.com/medvedevD/meeting-assistant) on
macOS with one command:

```sh
brew install --cask medvedevD/meeting-assistant/meeting-assistant
```

The app installs to `/Applications` and opens normally — no Gatekeeper
"cannot verify" wall, no Terminal commands.

<details>
<summary>Why is a special tap needed?</summary>

Meeting Assistant is currently an **ad-hoc-signed alpha** (not yet
Apple-notarized). A browser-downloaded DMG gets quarantined and walled off by
macOS Gatekeeper. This cask strips the quarantine attribute on install, so the
app launches cleanly. Notarized distribution (Apple Developer ID) is the planned
durable fix — see the main repository.

The central `homebrew/cask` tap does not accept un-notarized apps, which is why
this lives in a self-hosted tap.
</details>

## Update

```sh
brew upgrade --cask meeting-assistant
```

## Uninstall

```sh
brew uninstall --cask meeting-assistant        # remove the app
brew uninstall --zap --cask meeting-assistant  # also remove app data
```

---

`Casks/meeting-assistant.rb` is generated and published automatically by the
main repo's release workflow (`packaging/macos/render-release-cask.sh`). Do not
edit it by hand.
