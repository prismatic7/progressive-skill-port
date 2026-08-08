# progressive-skill Porting and Installation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Port `progressive-skill` to `antigravity-cli` and install it globally as an active plugin.

**Architecture:** Create standard `plugin.json` and `plugin.yaml` manifests, set up a virtual environment to verify the core Python tests, symlink the directory to `~/.gemini/config/plugins/`, and activate it in `config.json`.

**Tech Stack:** Python, JSON, YAML, Bash

## Global Constraints

- Must use Australian English spelling register (e.g. *optimisation*, *behaviour*).
- All files created must match paths exactly.
- Test suite verification must pass cleanly before global installation.

---

### Task 1: Scaffolding Manifests

**Files:**
- Create: `/Users/chris/Development/progressive-skill/plugin.json`
- Modify: `/Users/chris/Development/progressive-skill/plugin.yaml`

- [ ] **Step 1: Create `plugin.json`**
  Write a minimal `plugin.json` defining the plugin name:
  ```json
  {
    "name": "progressive-skill"
  }
  ```

- [ ] **Step 2: Update `plugin.yaml`**
  Verify the capabilities list in `plugin.yaml` to ensure it registers the skill:
  ```yaml
  name: progressive-skill
  version: 3.0.0
  description: "Smart skill index compaction — irrelevant categories collapse based on active toolset and usage frequency. Works with Antigravity CLI via cli.py and the progressive-skill skill."
  author: "LEO"
  license: MIT
  provides_skills:
    - progressive-skill
  ```

- [ ] **Step 3: Commit manifests**
  ```bash
  git add plugin.json plugin.yaml
  git commit -m "feat: add plugin manifests for progressive-skill"
  ```

---

### Task 2: Core Test Verification

**Files:**
- None (operational verification)

- [ ] **Step 1: Set up Python virtual environment**
  Create a virtual environment and install pytest to verify the decision core:
  ```bash
  python3 -m venv .venv
  .venv/bin/pip install pytest
  ```

- [ ] **Step 2: Run pytest**
  Run the test suite:
  ```bash
  .venv/bin/pytest tests/
  ```
  Verify all 11 unit tests pass.

- [ ] **Step 3: Clean up virtual environment**
  Remove the `.venv` folder to keep the repository clean:
  ```bash
  rm -rf .venv
  ```

---

### Task 3: Global Installation

**Files:**
- Modify: `/Users/chris/.gemini/config/config.json`

- [ ] **Step 1: Create global symlink**
  Symlink the repository to the global plugins folder:
  ```bash
  ln -sf /Users/chris/Development/progressive-skill /Users/chris/.gemini/config/plugins/progressive-skill
  ```

- [ ] **Step 2: Update `config.json`**
  Modify `/Users/chris/.gemini/config/config.json` to enable `"progressive-skill": { "enabled": true }`.

---

### Task 4: Integration Verification

**Files:**
- None (operational verification)

- [ ] **Step 1: Verify skill list**
  Run `agy --list-skills` or check the list of active skills using `agy` command to verify that `progressive-skill` is discovered.
