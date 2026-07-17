# Record snakes and coils in the hypercube (dimensions 9–13)

This repository is the dataset for the paper [A Census of New Snake-in-the-Box Records](https://arxiv.org/abs/2607.15270). The *snake-in-the-box* problem, introduced by Kautz in 1958, asks for
the longest induced (chordless) path — a *snake* — in the hypercube graph Qₙ; its maximum length a(n) is known only for n ≤ 8. We give snakes longer than the previous best-known in every dimension from 9 to 13, together with the longest known *coils* (induced cycles). Every record here is a machine-verifiable list of vertices in Qₙ.

## Snakes — `record_snakes.csv`

| n | a(n) (new) | previous | Δ | # distinct at record |
|---|-----------:|---------:|:--:|---------------------:|
| 9  | **191**  | 190  | +1  | 131 |
| 10 | **379**  | 376  | +3  | 12 |
| 11 | **746**  | 737  | +9  | 61 |
| 12 | **1476** | 1465 | +11 | ≥ 31,821 |
| 13 | **2922** | 2900 | +22 | ≥ 883 |

## Coils — `record_coils.csv`

| n | coil (new) | previous | Δ | # distinct at record |
|---|-----------:|---------:|:--:|---------------------:|
| 9  | **192** | 188 | +4 | 1 |
| 10 | **374** | 370 | +4 | 12 |
| 11 | **732** | 728 | +4 | 2 |

## Symmetric coils — `record_symmetric_coils.csv`

| n | coil (new) | previous | Δ | # distinct at record |
|---|-----------:|---------:|:--:|---------------------:|
| 10 | **370** | 362 | +8 | 2 |
| 11 | **726** | 718 | +8 | 1 |

"Distinct" counts are up to the full symmetry group of Qₙ (translation, axis permutation, and reversal — plus rotation, for coils). Dim-9's 131 is a believed-complete census; the other snake counts are distinct classes found so far (lower bounds).

## File format

Every file is CSV with columns `n,length,actions,vertices`:

- **actions** — the transition sequence: starting at the origin, flip coordinate `actions[0]`, then `actions[1]`, … For a coil the last action closes the cycle.
- **vertices** — the vertex list (integers), normalized to start at 0, so applying `actions` from 0 reproduces `vertices` exactly.

For a snake, `length` = number of edges = `len(actions)`; for a coil, `length` = number of vertices = number of edges.
