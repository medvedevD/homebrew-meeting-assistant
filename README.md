# Homebrew tap for Meeting Assistant

Install [Meeting Assistant](https://github.com/medvedevD/meeting-assistant) on
macOS:

```sh
brew tap medvedevd/meeting-assistant
brew install --cask meeting-assistant
```

On **Homebrew 6+**, the first install asks you to *trust* this tap — because the
cask removes the macOS quarantine flag for you (see below). Approve it by running
the `brew trust` command Homebrew prints, then re-run the install:

```sh
brew trust --cask medvedevd/meeting-assistant/meeting-assistant
brew install --cask meeting-assistant
```

The app installs to `/Applications` and opens normally — no Gatekeeper
"cannot verify" wall, no manual Terminal `xattr` commands.

<details>
<summary>Why is a special tap (and a trust prompt) needed?</summary>

Meeting Assistant is currently an **ad-hoc-signed alpha** (not yet
Apple-notarized). A browser-downloaded DMG gets quarantined and walled off by
macOS Gatekeeper. This cask strips the quarantine attribute on install, so the
app launches cleanly. That strip runs a command during install, which is why
Homebrew 6+ asks you to trust the tap once.

The central `homebrew/cask` tap does not accept un-notarized apps, which is why
this lives in a self-hosted tap. Notarized distribution (Apple Developer ID) is
the planned durable fix — see the main repository.
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
