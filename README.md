# toxwatch
# ToxWatch — Academic Research Project

Bachelor's thesis project at Academy of Econpmic Studies Bucharest, Faculty of  Cybernetics, Statistics and Economic Informatics, 2026.

**Title:** Application for the detection and analysis of online violence phenomena

## Overview

A microservices platform for detecting and quantifying toxic/abusive content
on public online communities. The system ingests public posts and comments
from social platforms (Hacker News, Reddit), scores them using established
toxicity-classification APIs (Google Perspective API), and aggregates the
results into a research dashboard used for the bachelor's thesis.

## Scope of Reddit API usage

- **Read-only access** via the official OAuth2 client_credentials flow.
- Endpoints used: `GET /r/{subreddit}/new.json` and
  `GET /r/{subreddit}/comments/{post_id}.json`.
- Poll frequency: 60s per subreddit. Well below the published rate limit.
- No posting, voting, messaging, moderation actions, or writes of any kind.
- No user-identifying data is ever exposed publicly; only aggregate statistics
  are presented in the research dashboard.

## Architecture

- **Language:** Go 1.22 (microservices), React + Vite (dashboard)
- **Message bus:** NATS
- **Storage:** MongoDB 7
- **External APIs:** Google Perspective (toxicity scoring)
- **Infrastructure:** Docker Compose (local development)

## Data handling

All collected data is stored on a locally hosted MongoDB instance controlled
by the researcher. No data is shared with third parties beyond the toxicity
classifier. The dataset is used solely for aggregate analysis in the thesis
and will not be redistributed.

## Source code

The full source code is maintained in a private repository during the thesis
defense period (academic integrity requirement). Access can be granted to
Reddit's API review team on request via email at andreea3mz@gmail.com
