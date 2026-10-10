# 🌿 Git & GitHub for DevOps: Complete Syllabus (with Definitions)

A module-by-module Git roadmap, from first commit to CI/CD workflows and history surgery. Every section starts with a short **Definition**. Tick the boxes as you go (`- [ ]` → `- [x]`).

> **Rule:** never just memorize commands. Create a throwaway repo, break it (bad merge, lost commit, wrong reset), then recover using `git reflog`.

**Prerequisites:** basic Linux command line.

## 📌 How to Use This Roadmap

| Priority | Modules | Why |
|---|---|---|
| 🟢 **Core (start here)** | 01–07 | Used every single day, asked in every interview |
| 🟡 **Next** | 08–11 | Team workflows and collaboration |
| 🔴 **Advanced** | 12–16 | CI/CD, security, recovery, large repos |
| 🏁 **Finish with** | 17 | Projects and interview prep |

## 📑 Table of Contents

1. [Version Control Fundamentals](#01-version-control-fundamentals)
2. [Installation & Configuration](#02-installation--configuration)
3. [Core Workflow](#03-core-workflow)
4. [Git Internals](#04-git-internals)
5. [Branching & Merging](#05-branching--merging)
6. [Remotes & Collaboration](#06-remotes--collaboration)
7. [Undoing Changes & Rewriting History](#07-undoing-changes--rewriting-history)
8. [Rebase, Cherry-pick, Stash & Tags](#08-rebase-cherry-pick-stash--tags)
9. [Advanced Tools](#09-advanced-tools)
10. [Branching Strategies & Workflows](#10-branching-strategies--workflows)
11. [GitHub / GitLab / Bitbucket](#11-github--gitlab--bitbucket)
12. [Git in CI/CD](#12-git-in-cicd)
13. [Git Security](#13-git-security)
14. [Customization & Configuration Files](#14-customization--configuration-files)
15. [Troubleshooting & Recovery](#15-troubleshooting--recovery)
16. [Large Repos, Monorepos & Performance](#16-large-repos-monorepos--performance)
17. [Capstones & Interview Prep](#17-capstones--interview-prep)

---

## 01. Version Control Fundamentals

### 1.1 What is Version Control
> **Definition:** A system that records changes to files over time so you can recall specific versions, compare them, and collaborate without overwriting each other.
- [ ] Why version control exists (history, collaboration, backup, rollback)
- [ ] Problems with manual versioning (`final_v2_REAL.zip`)

### 1.2 Types of Version Control Systems
> **Definition:** Categories based on where history is stored and how collaboration works.
- [ ] Local VCS (RCS)
- [ ] Centralized VCS (SVN, Perforce): single central server
- [ ] Distributed VCS (Git, Mercurial): every clone has full history

### 1.3 What is Git
> **Definition:** A free, open-source distributed version control system created by Linus Torvalds in 2005 for Linux kernel development.
- [ ] Snapshots vs deltas (how Git thinks about data)
- [ ] Nearly every operation is local and fast
- [ ] Integrity via SHA hashes (SHA-1, SHA-256 transition)
- [ ] Git vs GitHub vs GitLab vs Bitbucket

### 1.4 Core Vocabulary
> **Definition:** Terms used everywhere in Git documentation.
- [ ] **Repository:** the project plus its full history (`.git` directory)
- [ ] **Working tree:** the files you see and edit
- [ ] **Staging area (index):** the preparation area for the next commit
- [ ] **Commit:** a snapshot of the staged content with metadata
- [ ] **Branch:** a movable pointer to a commit
- [ ] **HEAD:** pointer to your current checkout (usually a branch)
- [ ] **Remote:** another copy of the repository (e.g. `origin`)
- [ ] **Clone / fork / upstream**

### 1.5 The Three States
> **Definition:** Files in Git live in one of three states: modified, staged, or committed.
- [ ] Working directory → staging area → repository
- [ ] Tracked vs untracked, ignored files

---

## 02. Installation & Configuration

### 2.1 Installing Git
> **Definition:** Getting the Git client onto your machine.
- [ ] Linux (`apt install git`, `dnf install git`), macOS, Windows (Git for Windows, WSL)
- [ ] Building from source (overview)
- [ ] `git --version`

### 2.2 Configuration Levels
> **Definition:** Git reads settings from three scopes, where narrower scopes override wider ones.
- [ ] `--system` (`/etc/gitconfig`)
- [ ] `--global` (`~/.gitconfig`)
- [ ] `--local` (`.git/config`)
- [ ] `git config --list --show-origin`

### 2.3 First-time Setup
> **Definition:** Minimum identity and behavior settings every user should set.
- [ ] `user.name`, `user.email`
- [ ] `core.editor`, `init.defaultBranch main`
- [ ] `pull.rebase`, `push.autoSetupRemote`
- [ ] `core.autocrlf` / `.gitattributes` (line endings)
- [ ] `credential.helper`

### 2.4 Getting Help
> **Definition:** Built-in documentation.
- [ ] `git help <cmd>`, `git <cmd> -h`, `man git-<cmd>`
- [ ] Pro Git book, `git help -a`, `git help -g`

### 2.5 Shell Productivity
- [ ] Bash/zsh completion, prompt branch indicator (`git-prompt.sh`)
- [ ] Oh My Zsh git plugin, aliases

---

## 03. Core Workflow

### 3.1 Creating Repositories
> **Definition:** Starting version control in a folder or copying an existing repository.
- [ ] `git init` (`--bare`, `-b main`)
- [ ] `git clone` (`--depth`, `--branch`, `--single-branch`, `--recurse-submodules`)
- [ ] HTTPS vs SSH URLs

### 3.2 Checking State
> **Definition:** Inspecting what has changed and what is staged.
- [ ] `git status` (`-s`, `-sb`)
- [ ] `git diff` (unstaged), `git diff --staged`, `git diff A..B`, `--stat`, `--name-only`
- [ ] `git show <commit>`

### 3.3 Staging
> **Definition:** Selecting which changes go into the next commit.
- [ ] `git add <file>`, `git add .`, `git add -A`, `git add -u`
- [ ] `git add -p` (interactive hunks)
- [ ] `git rm`, `git mv`, `git restore --staged`

### 3.4 Committing
> **Definition:** Recording a snapshot of the staged changes into history.
- [ ] `git commit -m`, `git commit -a`, `git commit --amend`
- [ ] Writing good commit messages (subject ≤ 50 chars, body explains why)
- [ ] Conventional Commits (`feat:`, `fix:`, `chore:`, `BREAKING CHANGE`)
- [ ] Atomic commits

### 3.5 Viewing History
> **Definition:** Browsing past commits.
- [ ] `git log` (`--oneline`, `--graph`, `--decorate`, `--all`)
- [ ] Filtering: `--author`, `--since`, `--grep`, `-S`, `-G`, `-- <path>`, `-p`, `--stat`
- [ ] Custom formats (`--pretty=format:`)
- [ ] `git shortlog -sn`, `git reflog`
- [ ] Revision syntax: `HEAD~2`, `HEAD^`, `main@{yesterday}`, `A..B`, `A...B`

### 3.6 Ignoring Files
> **Definition:** Telling Git which files not to track.
- [ ] `.gitignore` patterns, negation, directory rules
- [ ] `.git/info/exclude`, global ignore (`core.excludesFile`)
- [ ] Untracking an already tracked file (`git rm --cached`)
- [ ] `git check-ignore -v`

---

## 04. Git Internals

### 4.1 The `.git` Directory
> **Definition:** The folder that holds the entire repository database and metadata.
- [ ] `HEAD`, `config`, `index`, `objects/`, `refs/`, `hooks/`, `logs/`, `packed-refs`

### 4.2 Object Model
> **Definition:** Git is a content-addressable filesystem; everything is stored as objects named by their hash.
- [ ] **Blob:** file contents
- [ ] **Tree:** directory listing (names → blobs/trees)
- [ ] **Commit:** pointer to a tree, parent(s), author, message
- [ ] **Tag (annotated):** named, signed pointer to a commit
- [ ] Plumbing: `git cat-file`, `hash-object`, `ls-tree`, `write-tree`, `commit-tree`, `rev-parse`

### 4.3 References
> **Definition:** Human-readable names that point to commits.
- [ ] Branches (`refs/heads`), remote-tracking branches (`refs/remotes`), tags (`refs/tags`)
- [ ] `HEAD`, detached HEAD, symbolic refs
- [ ] `ORIG_HEAD`, `FETCH_HEAD`, `MERGE_HEAD`

### 4.4 The Index
> **Definition:** A binary file (`.git/index`) describing the proposed next commit.
- [ ] `git ls-files -s`, `git update-index`

### 4.5 Storage & Maintenance
> **Definition:** How Git stores and compacts data.
- [ ] Loose objects vs packfiles, delta compression
- [ ] `git gc`, `git prune`, `git fsck`, `git count-objects -vH`
- [ ] The commit DAG (directed acyclic graph)

---

## 05. Branching & Merging

### 5.1 Branch Basics
> **Definition:** A lightweight, movable pointer to a commit; creating one is nearly free.
- [ ] `git branch` (list, create, delete `-d` / `-D`, rename `-m`)
- [ ] `git switch`, `git switch -c`, `git checkout` (legacy)
- [ ] `git branch -vv`, `-a`, `-r`, `--merged`, `--no-merged`
- [ ] Naming conventions (`feature/`, `bugfix/`, `hotfix/`, `release/`)

### 5.2 Merging
> **Definition:** Combining the history of two branches.
- [ ] Fast-forward merge
- [ ] Three-way merge and merge commit
- [ ] `--no-ff`, `--ff-only`, `--squash`
- [ ] `git merge --abort`

### 5.3 Merge Conflicts
> **Definition:** A situation where Git cannot automatically reconcile changes to the same lines.
- [ ] Conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)
- [ ] Resolving manually, `git mergetool`, VS Code merge editor
- [ ] `git checkout --ours/--theirs`, `-X ours/theirs`
- [ ] `git diff --name-only --diff-filter=U`
- [ ] `git rerere` (reuse recorded resolutions)
- [ ] Preventing conflicts (small PRs, frequent syncing)

### 5.4 Merge Strategies
- [ ] `ort` (default), `recursive`, `octopus`, `ours`, `subtree`
- [ ] Merge base (`git merge-base`)

### 5.5 Comparing Branches
- [ ] `git diff main..feature`, `git diff main...feature`
- [ ] `git log main..feature`, `git cherry`

---

## 06. Remotes & Collaboration

### 6.1 Remotes
> **Definition:** Versions of your repository hosted elsewhere (server, GitHub, another folder).
- [ ] `git remote -v`, `add`, `remove`, `rename`, `set-url`, `show`
- [ ] `origin` vs `upstream` convention

### 6.2 Fetch, Pull, Push
> **Definition:** Commands that synchronize local and remote repositories.
- [ ] `git fetch` (download only, no merge), `--all`, `--prune`
- [ ] `git pull` = fetch + merge (or rebase with `--rebase`)
- [ ] `git push`, `-u` / `--set-upstream`, `--tags`, `--delete`
- [ ] `--force` vs `--force-with-lease` (and why the latter is safer)
- [ ] Remote-tracking branches (`origin/main`)

### 6.3 Authentication
- [ ] HTTPS + Personal Access Token
- [ ] SSH keys (`ssh-keygen -t ed25519`, `ssh-agent`, `~/.ssh/config`)
- [ ] Credential helpers (cache, store, manager)
- [ ] Deploy keys, fine-grained tokens, OIDC (CI)

### 6.4 Forking & Pull Requests
> **Definition:** A fork is your own server-side copy of someone else's repo; a pull request proposes merging your branch into theirs.
- [ ] Fork → clone → branch → commit → push → PR
- [ ] Keeping a fork in sync (`upstream` remote)
- [ ] Shared repository model vs fork model

### 6.5 Hosting Your Own Git Server
- [ ] Bare repositories, Git over SSH, `git daemon`
- [ ] Gitea, GitLab self-hosted (overview)

---

## 07. Undoing Changes & Rewriting History

### 7.1 Choosing the Right Undo
> **Definition:** Different commands undo changes at different stages; picking the wrong one loses work.

| Situation | Command |
|---|---|
| Discard unstaged edits | `git restore <file>` |
| Unstage a file | `git restore --staged <file>` |
| Fix last commit message/content | `git commit --amend` |
| Undo a pushed commit safely | `git revert <commit>` |
| Move branch pointer back | `git reset` |
| Recover "lost" commits | `git reflog` + `git reset` / `git branch` |

- [ ] Learn each row of this table hands-on

### 7.2 git restore / checkout
- [ ] `git restore`, `git restore --source=<commit>`
- [ ] `git checkout -- <file>` (legacy)

### 7.3 git reset
> **Definition:** Moves the current branch pointer to another commit, optionally changing index and working tree.
- [ ] `--soft` (keeps index + working tree)
- [ ] `--mixed` (default; resets index)
- [ ] `--hard` (resets everything, destructive)
- [ ] Reset vs revert on shared branches

### 7.4 git revert
> **Definition:** Creates a new commit that undoes the effect of an earlier commit, preserving history.
- [ ] Reverting merge commits (`-m 1`)
- [ ] Reverting a revert

### 7.5 Amending & Interactive Rebase
- [ ] `git commit --amend --no-edit`
- [ ] `git rebase -i` (`pick`, `reword`, `edit`, `squash`, `fixup`, `drop`, `reorder`)
- [ ] `git commit --fixup` + `git rebase -i --autosquash`
- [ ] Splitting a commit

### 7.6 Reflog: the Safety Net
> **Definition:** A local log of where `HEAD` and branch tips have been, letting you recover almost anything for ~90 days.
- [ ] `git reflog`, `HEAD@{n}`
- [ ] Recovering deleted branches and hard-reset commits

### 7.7 Golden Rule
- [ ] **Never rewrite history that others have already pulled** (shared branches)

---

## 08. Rebase, Cherry-pick, Stash & Tags

### 8.1 Rebase
> **Definition:** Re-applies your commits on top of another base commit, producing linear history.
- [ ] `git rebase main`, `--onto`, `--continue`, `--abort`, `--skip`
- [ ] Merge vs rebase trade-offs
- [ ] `pull --rebase`, `rebase --autostash`
- [ ] Why rebasing shared branches is dangerous

### 8.2 Cherry-pick
> **Definition:** Applies the changes of specific existing commits onto the current branch.
- [ ] `git cherry-pick <sha>`, ranges, `-x`, `-n`, `-m`
- [ ] Hotfix backport use case

### 8.3 Stash
> **Definition:** Temporarily shelves uncommitted changes so you can switch context.
- [ ] `git stash push -m`, `-u` (untracked), `-p`
- [ ] `list`, `show -p`, `apply`, `pop`, `drop`, `clear`, `branch`

### 8.4 Tags
> **Definition:** Named, fixed pointers to specific commits, typically used to mark releases.
- [ ] Lightweight vs annotated (`-a`) vs signed (`-s`) tags
- [ ] `git tag`, `git tag -d`, `git push origin <tag>`, `--tags`, `--delete`
- [ ] Semantic Versioning (`v1.2.3`)
- [ ] `git describe`

---

## 09. Advanced Tools

### 9.1 Finding Bugs
> **Definition:** Tools that search history to find which commit introduced a bug. `git bisect` does a binary search over commits.
- [ ] `git bisect` (`start`, `good`, `bad`, `run <script>`, `reset`)
- [ ] `git blame` (`-L`, `-w`, `-C`, `--ignore-rev`), `git log -S`, `git log -L`
- [ ] `git grep`

### 9.2 Worktrees
> **Definition:** Multiple working directories attached to a single repository, each on a different branch.
- [ ] `git worktree add/list/remove/prune`

### 9.3 Submodules & Subtrees
> **Definition:** Ways to embed one repository inside another.
- [ ] Submodules: `add`, `init`, `update --init --recursive`, pinning commits, pitfalls
- [ ] Subtree: `git subtree add/pull/push`
- [ ] Submodule vs subtree vs package managers

### 9.4 Hooks
> **Definition:** Scripts that Git runs automatically at certain events.
- [ ] Client: `pre-commit`, `prepare-commit-msg`, `commit-msg`, `pre-push`
- [ ] Server: `pre-receive`, `update`, `post-receive`
- [ ] Sharing hooks (`core.hooksPath`), tools: `pre-commit` framework, Husky, lefthook
- [ ] Use cases: linting, secret scanning, commit-message checks

### 9.5 Patches & Bundles
- [ ] `git format-patch`, `git apply`, `git am`
- [ ] `git bundle` (offline transfer), `git archive`

### 9.6 Cleaning & Housekeeping
- [ ] `git clean -fdn` (dry run first), `-fd`, `-fx`
- [ ] `git gc`, `git remote prune origin`, `git fetch --prune`
- [ ] Deleting merged branches in bulk

### 9.7 Partial & Shallow Clones
- [ ] `--depth`, `--filter=blob:none`, sparse-checkout
- [ ] `git sparse-checkout set <dir>`

### 9.8 Git LFS
> **Definition:** Git Large File Storage replaces large files with text pointers and stores contents on a separate server.
- [ ] `git lfs install`, `track`, `ls-files`, `.gitattributes`

### 9.9 Notes, Attributes & Misc
- [ ] `git notes`, `.gitattributes` (merge drivers, diff, `export-ignore`)
- [ ] `git range-diff`, `git diff --word-diff`, `git difftool`

---

## 10. Branching Strategies & Workflows

### 10.1 Centralized Workflow
- [ ] Everyone commits to `main`, rebase before push

### 10.2 Feature Branch Workflow
- [ ] Short-lived branch per feature, merged through PR

### 10.3 Git Flow
> **Definition:** A branching model with long-lived `main` and `develop` branches plus `feature`, `release`, and `hotfix` branches.
- [ ] Pros: structured releases; cons: complexity, slow integration

### 10.4 GitHub Flow
> **Definition:** A lightweight model: `main` is always deployable, every change goes through a short-lived branch and PR.

### 10.5 GitLab Flow
- [ ] Environment branches (`staging`, `production`), release branches

### 10.6 Trunk-Based Development
> **Definition:** Developers integrate small changes into a single trunk (`main`) at least daily, using feature flags to hide incomplete work.
- [ ] Short-lived branches, feature toggles, CI requirement
- [ ] Why high-performing DevOps teams prefer it

### 10.7 Release Management
- [ ] Release branches, tagging releases, hotfix & backport process
- [ ] Changelogs, release notes (auto-generated)

### 10.8 Merge Methods
- [ ] Merge commit vs squash and merge vs rebase and merge
- [ ] Choosing per team convention

### 10.9 Commit & PR Conventions
- [ ] Conventional Commits, PR templates, small PR size, linking issues

---

## 11. GitHub / GitLab / Bitbucket

### 11.1 Platform Basics
> **Definition:** Web platforms that host Git repositories and add collaboration features.
- [ ] Repos, organizations/groups, teams, roles and permissions
- [ ] Issues, labels, milestones, projects/boards
- [ ] Wikis, releases, GitHub Pages

### 11.2 Pull / Merge Requests
- [ ] Creating, reviewing, approving, suggesting changes
- [ ] Draft PRs, review comments, resolving threads
- [ ] Required reviewers, auto-merge, merge queue

### 11.3 Repository Protection
> **Definition:** Rules that stop unsafe changes from reaching important branches.
- [ ] Branch protection / rulesets (required reviews, status checks, signed commits, linear history)
- [ ] `CODEOWNERS`
- [ ] Restricting force pushes and branch deletion
- [ ] Tag protection

### 11.4 Platform Automation
- [ ] GitHub Actions (workflows, jobs, runners, secrets)
- [ ] GitLab CI (`.gitlab-ci.yml`)
- [ ] Webhooks, GitHub Apps, bots (Dependabot, Renovate)
- [ ] Templates: issue, PR, `.github/` folder, `CONTRIBUTING.md`, `SECURITY.md`

### 11.5 Access Management
- [ ] SSO / SAML, 2FA, PATs, deploy keys, service accounts
- [ ] Audit logs

### 11.6 CLI Tools
- [ ] GitHub CLI (`gh pr create`, `gh pr checkout`, `gh run`), `glab`

---

## 12. Git in CI/CD

### 12.1 Triggering Pipelines
> **Definition:** Pipelines start from Git events delivered by webhooks or polling.
- [ ] Webhook vs SCM polling (Jenkins "GitHub hook trigger")
- [ ] Push, PR, tag, schedule triggers
- [ ] Multibranch pipelines, branch/PR discovery

### 12.2 Jenkins + Git
- [ ] Git plugin, credentials (SSH key / PAT), `checkout scm`
- [ ] `git branch`, `GIT_COMMIT`, `GIT_BRANCH`, `changeset` conditions
- [ ] Shallow clone, sparse checkout, reference repos for speed

### 12.3 Versioning from Git
- [ ] `git describe --tags`, commit SHA in artifacts and image tags
- [ ] Semantic-release / release-please / standard-version
- [ ] Auto changelog from Conventional Commits

### 12.4 GitOps
> **Definition:** Using Git as the single source of truth for infrastructure and deployments; a controller reconciles the live state with Git.
- [ ] Pull-based deployment (Argo CD, Flux)
- [ ] Environment folders/branches, PR-based promotion
- [ ] Config repo vs app repo

### 12.5 Quality Gates
- [ ] Required status checks, pre-merge builds, signed commits
- [ ] Commit-lint and secret-scan in pipeline

### 12.6 Monorepo CI
- [ ] Path-based triggers, change detection (`git diff --name-only`)

---

## 13. Git Security

### 13.1 Authentication Security
- [ ] SSH key hygiene (ed25519, passphrase, agent), key rotation
- [ ] Token scope, expiry, least privilege

### 13.2 Signing Commits and Tags
> **Definition:** Cryptographically proving that a commit or tag came from you.
- [ ] GPG signing, SSH signing, `commit.gpgsign`, `git log --show-signature`
- [ ] "Verified" badge on GitHub

### 13.3 Secrets Leakage
> **Definition:** Credentials accidentally committed stay in history even after deletion.
- [ ] Detection: `gitleaks`, `trufflehog`, `git-secrets`, GitHub secret scanning
- [ ] Pre-commit hooks to block secrets
- [ ] **If a secret leaks: rotate it first**, then clean history
- [ ] Removing from history: `git filter-repo`, BFG Repo-Cleaner

### 13.4 Supply Chain
- [ ] Dependabot / Renovate, pinning GitHub Actions to SHAs
- [ ] Protecting `main`, mandatory reviews, CODEOWNERS for CI files

### 13.5 Data Privacy
- [ ] Private vs public repos, forks inherit visibility rules
- [ ] Sensitive data policy, `.gitignore` for env files

---

## 14. Customization & Configuration Files

### 14.1 Aliases
- [ ] `git config --global alias.st status`
- [ ] Useful aliases (`lg` for pretty graph log, `undo`, `amend`)

### 14.2 Config Details
- [ ] `includeIf` (different identity per folder), `url.<base>.insteadOf`
- [ ] `diff.tool`, `merge.tool`, `merge.conflictstyle zdiff3`
- [ ] `rerere.enabled`, `fetch.prune`, `rebase.autoStash`

### 14.3 `.gitattributes`
- [ ] Line endings (`text=auto eol=lf`), binary files, LFS, `linguist-*`

### 14.4 Templates
- [ ] `commit.template`, `init.templateDir`

### 14.5 Editor & GUI Tools
- [ ] VS Code Git, GitLens, lazygit, tig, GitKraken, Sourcetree

---

## 15. Troubleshooting & Recovery

### 15.1 Common Situations
- [ ] Detached HEAD: what it is and how to save the work (`git switch -c`)
- [ ] Committed to the wrong branch (cherry-pick + reset)
- [ ] Committed secrets or large files
- [ ] Pushed a bad commit (revert vs force push)
- [ ] Accidental `reset --hard` / deleted branch (reflog)
- [ ] Wrong merge (`git reset --hard ORIG_HEAD`, `revert -m 1`)
- [ ] Rebase gone wrong (`rebase --abort`, reflog)
- [ ] "Your branch has diverged" (pull vs rebase vs reset)
- [ ] Untracked files blocking checkout, `.gitignore` not working
- [ ] CRLF / line-ending diffs everywhere
- [ ] File-permission (`chmod`) changes showing in diff (`core.fileMode`)

### 15.2 Push / Pull Errors
- [ ] `rejected (non-fast-forward)`, `failed to push some refs`
- [ ] `refusing to merge unrelated histories`
- [ ] `Permission denied (publickey)`, `Authentication failed`
- [ ] `fatal: not a git repository`
- [ ] File > 100 MB rejected by GitHub
- [ ] `index.lock` exists, `unable to lock`
- [ ] `error: pathspec did not match`

### 15.3 Diagnostic Tools
- [ ] `git status`, `git log --graph --all --oneline`, `git reflog`
- [ ] `GIT_TRACE=1`, `GIT_CURL_VERBOSE=1`, `ssh -vT git@github.com`
- [ ] `git fsck --lost-found`, `git count-objects -vH`

### 15.4 Repository Cleanup
- [ ] Shrinking repositories (`git filter-repo`, `gc --aggressive`)
- [ ] Removing large files from history, rewriting author info
- [ ] Coordinating a history rewrite with the team

---

## 16. Large Repos, Monorepos & Performance

### 16.1 Performance Features
- [ ] Shallow/partial clones, sparse checkout, `--filter`
- [ ] `core.fsmonitor`, `feature.manyFiles`, commit-graph, multi-pack-index
- [ ] `git maintenance start`

### 16.2 Monorepo vs Polyrepo
> **Definition:** Monorepo keeps many projects in one repository; polyrepo uses one repository per project.
- [ ] Trade-offs: atomic changes vs access control and CI cost
- [ ] Tooling: Bazel, Nx, Turborepo, Lerna
- [ ] `CODEOWNERS` and path-filtered pipelines

### 16.3 Binary & Large Assets
- [ ] Git LFS, Git Annex, artifact repositories as alternative

### 16.4 Repository Migration
- [ ] SVN → Git (`git svn`), Mercurial → Git
- [ ] Moving between hosts (`git clone --mirror`, `git push --mirror`)
- [ ] Preserving history, splitting a folder into a new repo (`filter-repo --subdirectory-filter`)

---

## 17. Capstones & Interview Prep

### 17.1 Hands-on Labs
- [ ] Build a small repo, create 3 branches, force 2 different merge conflicts and resolve them
- [ ] Rewrite messy history into clean atomic commits with `rebase -i`
- [ ] Break-and-fix: `reset --hard`, delete a branch, then recover everything with `reflog`
- [ ] Use `bisect run` to find an intentionally introduced bug
- [ ] Accidentally commit a fake secret, then remove it with `git filter-repo`
- [ ] Set up pre-commit hooks (lint + secret scan + commit-msg check)
- [ ] Configure branch protection, `CODEOWNERS`, and required status checks on a GitHub repo
- [ ] Wire a Jenkins multibranch pipeline to a GitHub repo through webhooks
- [ ] Automate semantic versioning and releases from Conventional Commits

### 17.2 Interview Topics
- [ ] "Git vs GitHub?" / "Centralized vs distributed VCS?"
- [ ] "Explain the working directory, staging area, and repository."
- [ ] "`git fetch` vs `git pull`?"
- [ ] "`git merge` vs `git rebase`: when would you use each?"
- [ ] "`git reset` vs `git revert`; `--soft` vs `--mixed` vs `--hard`?"
- [ ] "How do you undo a commit that's already pushed?"
- [ ] "What is `HEAD`? What is detached HEAD?"
- [ ] "How do you resolve merge conflicts?"
- [ ] "What is `git stash`? `cherry-pick`? `bisect`?"
- [ ] "Explain Git Flow vs trunk-based development."
- [ ] "How do you remove a secret from Git history?"
- [ ] "How do you recover a deleted branch or lost commit?"
- [ ] "What is a bare repository? What are submodules?"
- [ ] "How does Git store data internally (blob, tree, commit)?"
- [ ] "How do you trigger a Jenkins build from a Git push?"
- [ ] "What is GitOps?"

### 17.3 Cheat Sheet
- [ ] Write your own one-page cheat sheet of the 30 commands you use most

---

## 🚀 What's Next

After Git, continue with: **CI/CD (Jenkins / GitHub Actions) → Docker → Terraform & Ansible → Kubernetes → GitOps (Argo CD)**.
