#!/usr/bin/env bash
set -euo pipefail

die() {
  printf '%s\n' "$*" >&2
  exit 1
}

Mise="$HOME/.local/bin/mise"

if command -v curl >/dev/null 2>&1; then
  curl -fsSL https://mise.run | sh
elif command -v wget >/dev/null 2>&1; then
  wget -qO - https://mise.run | sh
else
  die "curl or wget are required but neither is installed. Aborting."
fi

mkdir -p "$HOME/.ssh"
chmod 700 "$HOME/.ssh"

if command -v ssh-keyscan >/dev/null 2>&1; then
  ssh-keyscan github.com >> "$HOME/.ssh/known_hosts"
else
  die "ssh-keyscan is required to populate known_hosts."
fi

"$Mise" x gh -- gh auth login -p ssh -h github.com

"$Mise" x gh -- gh repo clone guria/dot "$HOME/.local/share/chezmoi"
"$Mise" x chezmoi -- chezmoi apply --init
