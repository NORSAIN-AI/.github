# .github
Standard policies, templates, and workflows for all NORSAIN repositories — centralizing CI/CD, security, and contribution guidelines.

## Workflows

### Reusable CI Workflow (`ci-reusable.yml`)

A reusable workflow that validates pull request requirements.

**Features:**
- ✅ Checks if PR has a milestone assigned
- ✅ Checks if PR has at least one label

**Usage in other repositories:**

```yaml
name: PR Validation
on:
  pull_request:
    types: [opened, synchronize, reopened, edited, labeled, unlabeled, milestoned, demilestoned]

jobs:
  validate:
    uses: NORSAIN-AI/.github/.github/workflows/ci-reusable.yml@main
```

**Configuration Options:**

Both checks are enabled by default. You can disable them individually:

```yaml
jobs:
  validate:
    uses: NORSAIN-AI/.github/.github/workflows/ci-reusable.yml@main
    with:
      check-milestone: false  # Skip milestone check
      check-labels: true      # Keep label check
```

### Example Workflow (`pr-checks.yml`)

An example implementation showing how to use the reusable workflow in this repository.
