# dumpster-toolchain

Engines used by **dumpster**, a local workbench for dumping decrypted iOS apps. Each engine lives in its own folder with its upstream history and license. `toolchain.json` lists the engines, their entry points, and the Frida versions they are tested against.

This repo holds engine **source only**. Frida, Python packages, and compiled binaries are installed at runtime by the consumer, never committed.

| Engine | Platform | Status | Upstream |
|---|---|---|---|
| [frida-ios-dump-modern](frida-ios-dump-modern/) | iOS | integrated | [jwalker/frida-ios-dump-modern](https://github.com/jwalker/frida-ios-dump-modern) |
| frida-ipa-extract | iOS | planned | [lautarovculic/frida-ipa-extract](https://github.com/lautarovculic/frida-ipa-extract) |
| iDump | iOS | planned | [Fi5t/iDump](https://github.com/Fi5t/iDump) |

## Use it standalone

```sh
cd frida-ios-dump-modern
python3 -m venv .venv && .venv/bin/pip install -r requirements.txt
.venv/bin/python dump.py --help
```

Match the host `frida` version to the `frida-server` running on the phone.

## Pulling upstream fixes

Engines are git subtrees, so upstream history is preserved:

```sh
git subtree pull --prefix=frida-ios-dump-modern https://github.com/jwalker/frida-ios-dump-modern main
```

Resolve conflicts against the local hardening commits, then tag a release (`vX.Y.Z`). Consumers pin tags.

## Legal

Only use these tools on apps and devices you own or are explicitly authorized to test. See [NOTICE](NOTICE) for third-party licenses.
