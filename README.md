# fsaie

My working repo for the Towards AI **Full Stack AI Engineering** course. Reflections, observations and corrections as I go, rebuilt on a current Python stack (LiteLLM, multi-provider) instead of the dated course code.

> Status: early. Structure and stack decisions are still being made and will change as the course progresses.

## Why this repo exists

The course teaches a sound sequence: data, prompting, RAG, fine-tuning, agents, feedback loops and UI. Some of its code and setup is dated (Colab notebooks, single-provider OpenAI calls, older SDK patterns). This repo keeps the sequence, replaces the dated parts, and records why.

It serves two goals:

1. **A repeatable project structure** I can reuse for future AI projects.
2. **An end-to-end agentic coding process** for building those projects with coding agents.

## Stack decisions so far

| Area | Decision |
|---|---|
| Language | Python only |
| Environment | Local repo, `uv` with a lockfile, `.env` kept out of git |
| LLM access | LiteLLM as the single gateway for all model calls |
| Providers | OpenAI, Anthropic, xAI. OpenRouter and Ollama for experiments |
| Model choice | Code asks for a role (fast, strong, embedding, judge); config maps each role to a model, chosen by testing on my own cases |
| Cost | Token usage and cost logged on every call; prices kept in config with the date checked |
| Deployment | Vercel (details to be settled) |

## Repo layout (planned)

```
fsaie/
  README.md
  pyproject.toml
  uv.lock
  .env.example        # API key names, no values
  config/
    models.yaml       # role to provider/model, price, date checked
  src/fsaie/          # shared code: model client, cost tracking
  lessons/            # one folder per lesson: code plus a short reflection
  tests/              # unit tests with a fake model, no API calls
  docs/
    to-do/            # plans not started
    in-progress/      # plans being worked on
    done/             # shipped plans
    uat/              # one UAT log per major version
```

## Setup

```bash
git clone https://github.com/sbdatasc/fsaie.git
cd fsaie
uv sync
cp .env.example .env   # then add your own API keys
```

## Progress

| Lesson | Topic | Reflection |
|---|---|---|
| FSAIE 01 | From Beginner to Advanced LLM Developer | Course map; one project from data to deployment |
| FSAIE 02 | Introduction and the LLM application stack | Build bottom up; add evaluation as a layer across the whole stack |
| FSAIE 03 | Syllabus | Parts 0 to 4; Part 4 is my own LLM and RAG project |
| FSAIE 04 | LLM setup and usage | Course code dated; corrections recorded, move to a multi-provider setup |

## Course

[From Beginner to Advanced LLM Developer](https://academy.towardsai.net/courses/beginner-to-advanced-llm-dev), Towards AI Academy.

This repo holds my own notes and code. It does not reproduce course material.
