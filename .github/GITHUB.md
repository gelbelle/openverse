# .github

This folder contains files that configure GitHub services for the management of
the Openverse project.

## Workflows

### Project automation

This workflow move issues with linked PRs from the "Backlog" and "To do" columns 
to the "In progress" column.

**Cron:** [at every 15th minute](https://crontab.guru/#*/15_*_*_*_*)
**Dispatch:** enabled

### New issue automation

This workflow adds issues to the "Backlog" column in the Openverse project as
soon as they are created.

**Issue:** opened
**Dispatch:** disabled

### New PR automation

This workflow adds PRs to the "In progress" or "Needs review" columns based on 
whether they are marked as draft or ready.

**PR:** opened, converted_to_draft, ready_for_review
**Dispatch:** disabled

### Label sync

This workflow ensures that all repos associated with the project have the
minimum set of consistent labels. It creates missing labels, and updates the 
color and description where they do not match the standard values.

**Cron:** [at 00:00](https://crontab.guru/#0_0_*_*_*)
**Dispatch:** enabled

### Meta file sync

This workflow ensures that the files specified in [`sync.yml`](sync.yml) are
synchronised across all Openverse repos. Treating this repo as the source of
truth, it creates PRs to resolve any differences.

**Cron:** [at 00:00](https://crontab.guru/#0_0_*_*_*)
**Push:** Glob `.github/**`
**Dispatch:** enabled