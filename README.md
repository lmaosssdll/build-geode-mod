# 🔨 Universal Geode Mod Builder

A GitHub Actions workflow that can **build any [Geode](https://geode-sdk.org/) mod**
from source — just by providing a repository URL and branch name.

No need to fork, configure CI, or install anything locally.

---

## 🚀 How to Use

1. Go to the **[Actions](../../actions)** tab
2. Select **"Build ANY Geode Mod"** workflow
3. Click **"Run workflow"**
4. Fill in the fields:

| Field | Description | Example |
|-------|-------------|---------|
| **Mod repo** | GitHub URL of the mod | `https://github.com/techstudent10/creation-rotation` |
| **Branch** | Branch or tag to build | `main` |

5. Click **"Run workflow"** ▶️
6. Wait for the build to complete (~5-10 minutes)
7. Download the `.geode` file from **Artifacts**

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🔗 **Any repo** | Just paste a GitHub URL — no forking needed |
| 🌿 **Any branch/tag** | Build from `main`, `dev`, `v1.0.0`, etc. |
| 📦 **Auto SDK version** | Reads `mod.json` / `geode.json` and installs the correct Geode SDK |
| 💾 **SDK caching** | Geode SDK is cached between builds — faster rebuilds |
| 🔄 **CMake fallback** | If `geode build` fails, automatically tries raw CMake |
| 📥 **Auto dependencies** | Runs `geode install` to fetch mod dependencies |
| 🏷️ **Smart naming** | Artifact is named `mod-id-version` automatically |

---

## 📋 Requirements

- The mod repository must be **public** (or you need to configure access tokens)
- The mod must use **Geode SDK** and have a valid `mod.json` or `geode.json`
- The mod must be buildable with `geode build` or standard CMake

---

## 🔧 How It Works
Clone mod repo (with submodules)
↓
Parse mod.json → extract Geode SDK version
↓
Install Geode CLI (latest)
↓
Clone/cache Geode SDK (matching version)
↓
Install SDK binaries + mod dependencies
↓
Build: geode build → fallback to CMake if needed
↓
Upload .geode artifact
text


---

## 📁 Example Mods You Can Build

| Mod | Repo | Branch |
|-----|------|--------|
| Creation Rotation | `https://github.com/techstudent10/creation-rotation` | `main` |
| BetterEdit | `https://github.com/HJfod/BetterEdit` | `main` |
| Globed | `https://github.com/GlobedGD/globed2` | `main` |
| *Any Geode mod...* | *Any GitHub URL* | *Any branch* |

> ⚠️ Some complex mods may require additional setup (Rust toolchain, custom
> dependencies, etc.) and might not build with this workflow alone.

---

## 🐛 Troubleshooting

### Build fails with "No mod.json found"
The mod might use a different project structure. Check if `mod.json` is in a
subdirectory.

### Build fails at CMake stage
The mod might need specific CMake flags or dependencies not covered by this
workflow. Check the mod's own CI configuration for hints.

### SDK version mismatch
If the mod requires a pre-release/beta version of Geode SDK that doesn't have a
matching git tag, the clone step will fail. Try specifying the exact tag in the
branch field.

---

## 📄 License

MIT — use freely, modify, share.

---

*Built with ❤️ for the Geometry Dash modding community*
