---
name: vault-backup
display_name: Vault Backup
description: "Universal secure backup — encrypt (AES-256), compress (zstd), deduplicate, verify integrity. Backup project files, databases, .claude/ setup, configs. Incremental, secrets-aware, multi-destination."
version: 1.0.0
author: cognittusai
license: MIT
tags:
  - "backup"
  - "security"
  - "encryption"
  - "compression"
  - "devops"
  - "disaster-recovery"
marketplace_url: "https://myclaude.sh/p/vault-backup"
user-invocable: true
---

# Vault Backup


> Universal secure backup — encrypt, compress, deduplicate, verify.


## The Problem

You have projects, databases, configs, Claude Code setups scattered across your machine. One disk failure, one accidental `rm -rf`, one ransomware attack — and it's gone. Generic backup tools don't understand your development workflow. They backup everything (including node_modules and .git) or nothing useful.

**Vault Backup** is a Claude Code skill that understands what matters: your code, your configs, your databases, your `.claude/` setup. It excludes what doesn't (node_modules, build artifacts) and protects what's sensitive (encrypts by default, never backs up raw secrets).

## Install

```bash
myclaude install vault-backup
```

## Is this for me?

**Yes if:**
- You want automated, encrypted backups from Claude Code
- You need to backup databases (Supabase, Postgres, MySQL)
- You want incremental backups that save space
- You need integrity verification for your backups

**No if:**
- You need enterprise backup with SLA (use Veeam, Commvault)
- You need real-time replication (use database native tools)

## Quick Start

```
/vault-backup quick                    # snapshot critical files
/vault-backup full --encrypt           # complete backup with AES-256
/vault-backup restore ./backups/latest # restore from backup
/vault-backup verify ./backups/latest  # check integrity
```

## Features

### Security First
- **AES-256-GCM encryption** via `age` — enabled by default, not optional
- **Secrets-aware** — automatically excludes .env, .p12, credentials, tokens
- **Integrity verification** — SHA-256 hash per archive + per-file hashes in manifest
- **Key safety** — passphrase never stored in the backup itself

### Space Optimization
- **zstd compression** — 60-75% reduction on typical projects
- **Incremental backups** — only changed files since last backup
- **Smart exclusion** — skips node_modules, .git objects, build artifacts, cache
- **Retention policy** — auto-cleanup old backups (default: keep last 5)

### Multi-Target
- **Project files** — source code, configs, docs
- **Claude Code setup** — .claude/ rules, skills, commands, memories
- **Databases** — Supabase, Postgres (pg_dump), MySQL, SQLite
- **System configs** — .gitconfig, .ssh/config, .env.example

### Multi-Destination
- **Local** — project directory or external drive
- **Cloud** — S3, Backblaze B2, Google Drive (via rclone)
- **Git** — dedicated backup branch (for small projects)

### Developer-Friendly
- **4 modes** — quick, full, restore, verify
- **One command** — discovers, excludes, compresses, encrypts, verifies
- **Cross-platform** — macOS, Linux, Windows (WSL)
- **Manifest** — JSON manifest with every file, hash, and metadata

## How It Works

```
/vault-backup quick
```

1. **Discover** — scans target path, builds file inventory
2. **Exclude** — removes secrets, build artifacts, large binaries
3. **Compress** — zstd compression (level 3 quick, level 9 full)
4. **Encrypt** — AES-256-GCM via age (default on)
5. **Verify** — SHA-256 integrity check
6. **Report** — summary with file count, size, ratio, hash
7. **Cleanup** — remove old backups beyond retention limit

Each step is logged and any failure is reported immediately — no silent data loss.

## Requirements

- Claude Code CLI
- `tar` and `zstd` (pre-installed on macOS/Linux, available via WSL on Windows)
- `age` for encryption (optional, recommended)
- `rclone` for cloud destinations (optional)

## Compatibility

- macOS, Linux, Windows (WSL)
- Claude Code v1.0+

## Language

EN | PT-BR | ES — auto-detects from your conversation language.

## License

Proprietary — © 2026 CognittusAI

---

*Built with [MyClaude Studio Engine](https://myclaude.sh)*

---

[![MCS-2](https://myclaude.sh/badge/mcs/2.svg)](https://myclaude.sh/quality)
[![Available on MyClaude](https://myclaude.sh/badge/available.svg)](https://myclaude.sh/p/vault-backup)

<sub>Built with MyClaude Studio Engine</sub>

