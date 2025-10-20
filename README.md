# ⚡ Optimize Build Disk Space

**Removes unused SDKs, tools, and cached files to free up space for your GitHub Actions builds.**

This action safely deletes preinstalled software and cached files on GitHub-hosted Ubuntu runners, reclaiming up to **30 GB of additional disk space**.  
Perfect for large builds such as Android ROMs, Docker images, or kernel compilation.

---

## ✨ Features

- 🧹 Remove unused SDKs and tools (.NET, Android, Haskell, etc.)
- 🗑️ Clear cached setup tools and temporary files
- 🐋 Optionally prune Docker images
- 🧠 Create a fresh 4 GB swapfile
- 💬 Optional verbose and disk usage reports
- ⚡ Fully parallel cleanup for faster execution

---

## 🚀 Example Usage

Add this step **before your build** to maximize free space.

```yaml
name: Build with optimized disk space
on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: 🚀 Optimize Build Disk Space
        uses: TukangHantam/optimize-build-space@main
        with:
          remove-dotnet: 'true'         # Frees ~2 GB
          remove-haskell: 'true'        # Frees ~5.2 GB
          remove-codeql: 'true'         # Frees ~5.4 GB
          remove-docker-images: 'true'  # Frees ~3.2 GB
          verbose: 'true'               # Show detailed logging of the action
          show-disk-space: 'true'       # Show disk space

      - name: Checkout code
        uses: actions/checkout@v4
