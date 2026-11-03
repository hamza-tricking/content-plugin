---
name: audience
description: Analyses the creator's followers and viewers themselves: who they are (country, gender, age, active times), what they say in comments (keywords, thanks, questions, requests), and which videos bring followers. Use after onboarding data extraction, before strategy, when the user asks "who are my followers" or "what do they ask", and in the monthly review.
---

# Audience analysis

Goal: understand the people, not only the numbers. Work in aggregate: never store usernames or individual accounts; never contact anyone.

## 1. Who they are
From the sources the user has set up (Instagram insights, TikTok Studio followers tab, Metricool demographics): country, gender, age, share of views from non-followers, where views come from (feed, For You, profile, search), most active times.
- Compare viewers vs followers and platform vs platform; say these are different measures and the difference is a hint, not proof.
- Report unexplained shares (for example a large "Others") as unexplained.

## 2. What they say
Read the real comments (via Claude in Chrome on the creator's own studio/comments pages). Read all that are available in the window; say how many and from what period. If only a few were read, say so.
Classify:
- keyword replies to a call to action (these are not opinions; count them separately),
- thanks, praise, prayers,
- emoji only,
- questions and requests (explain-more, how-to, topic requests),
- objections or criticism.
Quote only short, anonymized wording of questions and requests.

## 3. Which videos bring followers
Where the platform shows follower gain per video, compare videos by new followers, not only views. If it is not available, say so and use views vs followers over time.

## 4. Output: `dna/audience.md`
Tables for who they are and what they say, a short "what it suggests" list marked as hypotheses with the sample size, and a "next" list of what was not read. The user confirms it before it feeds the strategy.

## 5. Use
- Feed the strategy: topics requested, clarity problems (repeated "how?" on one video), tone and level.
- Re-run monthly and in the day-30 review; compare shares with the previous version.
- Follow the `examples` skill: turn a real request from the comments into a worked example, if the user wants.
