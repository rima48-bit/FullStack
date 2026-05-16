### Contributor setup notes

**Verify prerequisites before cloning**
- `rustc --version` — 1.77+
- `node --version` — 20+

**Windows:** Keep the project outside OneDrive. Cargo writes thousands
of small files to `target/` and OneDrive locks them mid-build, causing
`Access is denied (os error 5)`. Use a path like `C:\dev\nova`.

**Icons:** `src-tauri/icons/` is not committed to the repo. On Windows
the first build will fail with `` `icons/icon.ico` not found ``. Fix:
```bash
npx tauri icon "your-image.png"  # any square PNG works
```

**Linux:** The apt-get block above may need these additional packages
depending on your distro version:
```bash
build-essential libxdo-dev libgtk-3-dev
```

**Clean install:** Always use `npm ci` not `npm install`.
On Windows: `Remove-Item -Recurse -Force node_modules` to clear the folder.

**Version mismatch warning:** A warning about mismatched Rust/npm versions
is cosmetic — do not bump npm package versions to match.
```sh
rustup target add aarch64-apple-darwin x86_64-apple-darwin
npm run tauri build -- --target universal-apple-darwin
