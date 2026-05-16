### Contributor setup notes

**Verify prerequisites before cloning**
- `rustc --version` — 1.77+
- `node --version` — 20+
- `npx tauri --version` — Tauri CLI 2.x

**Windows:** Keep the project outside OneDrive. Cargo writes thousands
of small files to `target/` and OneDrive locks them mid-build, causing
`Access is denied (os error 5)`. Use a path like `C:\dev\nova`.

**Icons(first build requirement):** `src-tauri/icons/` is not committed to the repository. On first build, Windows users may see: `` `icons/icon.ico` not found ``. Fix:
```bash
npx tauri icon "your-image.png"  # any square PNG works
```

**Linux:** The apt-get block above may need these additional packages
depending on your distro version:
```bash
sudo apt-get install build-essential libxdo-dev libgtk-3-dev
```

**Clean install:** Always use lockfile-based install: `npm ci` not `npm install`.
To reset dependencies on Windows: `Remove-Item -Recurse -Force node_modules`.

**Version mismatch warning:** A warning about mismatched Rust/npm versions
is cosmetic — Do not upgrade dependencies solely to match versions
            —  The project will still build and run correctly
