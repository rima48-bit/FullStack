### Contributor setup notes

**Verify prerequisites before cloning**

| Tool | Minimum | Check |
|------|---------|-------|
| Rust (stable) | 1.77+ | `rustc --version` |
| Node.js | 20+ | `node --version` |
| Tauri CLI | 2.x | `npx tauri --version` |

**Windows — move the project out of OneDrive**

Cargo writes thousands of small files to `target/` during compilation.
OneDrive locks these files mid-build and causes:
Access is denied. (os error 5)

Clone or move the project to a plain path like `C:\dev\nova`.

**Icons — required before first build**

`src-tauri/icons/` is not committed to the repo. On first clone, the build will fail with:icons/icon.ico not found; required for generating a Windows Resource file
Generate them once from any square PNG:

```bash
npx tauri icon "your-image.png"
```

**Linux — additional packages**

Depending on your distro version, the `apt-get` block above may also need:

```bash
sudo apt-get install build-essential libxdo-dev libgtk-3-dev
```

**Dependencies**

Always use `npm ci` (not `npm install`) to install from the lockfile exactly.
On Windows, to reset `node_modules`:

```bash
Remove-Item -Recurse -Force node_modules
```

**Version mismatch warning**

You may see a warning about mismatched Rust crate and npm package versions.
This is cosmetic — do not upgrade packages to match. The project will build and run correctly.
