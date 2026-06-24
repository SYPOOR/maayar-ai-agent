---
name: Architecture Question
description: Ask an architecture question or propose a design change
title: "[Architecture] "
labels: ["architecture"]
body:
  - type: markdown
    attributes:
      value: |
        Use this template for architecture questions or design proposals. For formal decisions, submit an ADR via pull request.

  - type: textarea
    id: question
    attributes:
      label: Question or Proposal
      description: What architecture question do you have or what change do you propose?
      placeholder: Should the Disease Exposure capability also consume satellite imagery directly?
    validations:
      required: true

  - type: dropdown
    id: area
    attributes:
      label: Architecture Area
      options:
        - Agent Orchestration
        - Intelligence Layer / Capabilities
        - Risk Engine
        - Data Layer
        - Infrastructure
        - API Design
        - Other
    validations:
      required: true

  - type: textarea
    id: context
    attributes:
      label: Context
      description: What context or motivation drives this question?
      placeholder: As we scale to portfolio-level assessments...

  - type: textarea
    id: alternatives
    attributes:
      label: Alternatives Considered
      description: If proposing a change, what alternatives have you considered?
