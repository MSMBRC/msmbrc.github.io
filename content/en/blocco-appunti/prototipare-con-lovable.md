---
title: "Prototyping with Lovable"
date: 2026-01-03
draft: false
type: "blocco-appunti"
layout: "single"
---

I used Lovable to build a web app prototype — a tool for managing and evaluating suppliers. Document uploads, deadlines, ratings, dashboard, communications.

The workflow was simple and repetitive: I described each part of the application as the structure took shape, turned the requests into optimised prompts for Lovable, checked the output and went back to chat to refine. This approach allowed rapid iterations, fixing only what surfaced each time around.

## Workflow

Describe → generate the prompt → paste into Lovable → verify → correct. Each cycle took a few minutes. No waste, no rewriting from scratch.

## What needed refining

Data consistency between supplier lists and detail views was the trickiest part. The document expiry logic, file categories, and rating fields (numeric, range, lists) needed several passes to become coherent. The same goes for communications and email templates.

Menu visibility based on user type — admin vs. supplier — was one of the last things to fix, but one of the most important. All of this without ever touching the core logic already generated: just clarifying and making consistent what Lovable was supposed to produce.

## Result

The prototype is complete and covers all main pages and interactions. It can be turned into the final product using the existing design system, without starting from scratch.

{{< nota tipo="processo" >}}
Tools used: [Lovable](https://lovable.dev) · [Copilot](https://copilot.microsoft.com/)
{{< /nota >}}
