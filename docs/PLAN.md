# Pricing / Revenue Management Data Science — Learning Plan

Status key: `[ ]` not started · `[~]` in progress · `[x]` done

Started: 2026-10-23

## Goal

Build sound theory and a portfolio-ready GitHub repo in pricing / revenue
management data science — the umbrella field covering dynamic pricing,
revenue management, and price optimization across airlines, ride-hailing,
e-commerce, insurance, logistics, and ticketing. Bridge explicitly from an
adtech/RTB-auctions background (contextual bandits for pricing are
mechanically the same loop as bid optimization in RTB).

Primary text: Talluri & van Ryzin, *The Theory and Practice of Revenue
Management* (Springer, 2004, 713pp, 11 chapters). Exact per-chapter page
counts not yet confirmed — recalibrate pacing below once known.

Confirmed chapter list:
1. Introduction (pp. 1–24)
2. Single-Resource Capacity Control
3. Network Capacity Control
4. Overbooking
5. Dynamic Pricing
6. Auctions
7. Customer-Behavior and Market-Response Models
8. The Economics of RM
9. Estimation and Forecasting
10. Industry Profiles
11. Implementation

## Datasets

- **Hotel Booking Demand** (Antonio, Almeida & Nunes 2019) — 119,390 rows, includes `adr` (avg daily rate)
- **Dominick's / Kilts Center scanner data** (Chicago Booth) — ~98.7M price observations; requires requesting academic-use access, kick off early
- **Chicago rideshare trips** (City of Chicago open data) — trip-level since Nov 2018, no explicit surge field — used to reverse-engineer dynamic pricing

## Tooling

Forecasting: `statsforecast`, scikit-learn · Bayesian: PyMC + ArviZ ·
Optimization: `cvxpy`, OR-Tools/PuLP · Causal: DoWhy, EconML, `diff-diff` ·
Bandits: Vowpal Wabbit (contextual) or hand-rolled ε-greedy/UCB/Thompson

## Week-by-week plan

| Wk | Status | Book reading | Practice | Dataset/tool |
|---|---|---|---|---|
| 1 | [ ] | Ch.1 Introduction (~24pp, light) | Repo setup (this repo). Kick off Dominick's/Kilts academic-access request. Download Hotel Booking Demand + Chicago rideshare data. | — |
| 2 | [ ] | Ch.2 Single-Resource Capacity Control, part 1 (Littlewood's rule) | Implement Littlewood's two-class rule from scratch on a toy booking-curve. | synthetic |
| 3 | [ ] | Ch.2 cont'd (EMSR-a, EMSR-b) | Implement EMSR-a then EMSR-b; validate against the `revmng` PyPI package. | synthetic |
| 4 | [ ] | *(consolidate Ch.2, no new reading)* | Multi-class airline booking-curve simulator; show revenue lift of EMSR-b vs. naive fixed allocation. Write `src/rm_control/README.md`. | synthetic |
| 5 | [ ] | Ch.3 Network Capacity Control, part 1 | Formulate a 2–3 leg network RM problem as an LP (bid-price control) with `cvxpy`/PuLP. | synthetic |
| 6 | [ ] | Ch.3 cont'd | Finish bid-price control; compare single-resource vs. network allocation. | synthetic |
| 7 | [ ] | Ch.4 Overbooking (shorter — buffer week) | Add overbooking-risk layer to the simulator (optional: cancellation-probability model). | — |
| 8 | [ ] | Ch.7 Customer-Behavior & Market-Response Models | Start elasticity module: log-log demand regression. | Dominick's |
| 9 | [ ] | *(consolidate elasticity work)* | Bayesian elasticity in PyMC — per-SKU estimates, partial pooling, cross-price effects, posterior uncertainty. | Dominick's |
| 10 | [ ] | Ch.8 The Economics of RM (conceptual) | Write up elasticity module as a standalone case study. | Dominick's |
| 11 | [ ] | Ch.9 Estimation and Forecasting | `statsforecast` demand forecast on Hotel Booking Demand — feeds the capstone's RM-control step later. | Hotel Booking Demand |
| 12 | [ ] | Ch.5 Dynamic Pricing, part 1 | Non-contextual bandits (ε-greedy, UCB, Thompson Sampling) in a synthetic willingness-to-pay pricing simulator. | synthetic |
| 13 | [ ] | Ch.5 cont'd | Compare bandit strategies' regret curves; write up. | synthetic |
| 14 | [ ] | Ch.6 Auctions + light Krishna *Auction Theory* skim | Contextual bandit via Vowpal Wabbit tutorial. Write the explicit RTB-auction parallel into the README. | VW tutorial |
| 15 | [ ] | *(no book — DoWhy's own causal-inference tutorial)* | Diff-in-differences on Chicago rideshare data (or a natural rate-change window in Hotel Booking Demand) with `diff-diff`. | Chicago rideshare |
| 16 | [ ] | Ch.10 Industry Profiles (note how each maps to job postings already found) | EconML double-ML for heterogeneous elasticity by segment. | Dominick's / rideshare |
| 17 | [ ] | Ch.11 Implementation (practical/organizational) | Begin capstone: chain forecast → RM/optimization → bandit explore/exploit → causal evaluation into one pipeline. | Hotel Booking Demand |
| 18 | [ ] | *(book finished — review weak spots)* | Finish capstone; write `docs/capstone_writeup.md` as an interview-style case study. Resume scanning live postings (Allegro/ERGO alerts). | Hotel Booking Demand |

## Recalibration notes

(Add actual chapter page numbers here once confirmed from the physical book, to tighten weekly pacing.)

## Job-market tracking (resume once skillset is built, per week 18)

Strongest recurring-hiring signals found so far (2026-10-23 research):
- **Allegro** (Warsaw/Poznań, hybrid) — "Data Scientist, Pricing" titles recur
- **ERGO Technology & Services** (Warsaw + Gdańsk, hybrid/remote-option) — actuarial pricing, recurs
- Set direct job alerts on both career pages rather than relying on point-in-time search.

## Log

- 2026-10-23: Plan created, repo scaffolded, Week 1 structure in place.
