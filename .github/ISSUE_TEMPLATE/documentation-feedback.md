---
name: Documentation Feedback
description: Report documentation issues or suggest improvements
title: "[Docs] "
labels: ["documentation"]
body:
  - type: markdown
    attributes:
      value: |
        Thanks for helping improve Maayar's documentation. Please provide as much detail as possible.

  - type: textarea
    id: description
    attributes:
      label: Description
      description: What documentation issue did you find or what improvement do you suggest?
      placeholder: The Intelligence Orchestration page is missing information about...
    validations:
      required: true

  - type: input
    id: page
    attributes:
      label: Affected Page
      description: Which document or page is affected?
      placeholder: architecture/agent-x-orchestrator.md
    validations:
      required: true

  - type: dropdown
    id: type
    attributes:
      label: Issue Type
      options:
        - Typo or grammatical error
        - Broken link
        - Outdated information
        - Missing content
        - Clarity improvement
        - Other
    validations:
      required: true

  - type: textarea
    id: suggestion
    attributes:
      label: Suggested Fix
      description: If you have a suggestion for how to fix or improve, describe it here.
      placeholder: I suggest adding a section about...
