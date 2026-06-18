# \_perf — perf zsh completion

Ref: [`perf.bash`](perf.bash) (bash reference)

## Changes from bash version

| Area              | bash `perf.bash`                                                  | zsh `_perf`                                                                   |
| ----------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| Data source       | `perf list hw sw cache pmu tracepoint event_glob` + regex parsing | `perf list --raw-dump hw sw cache tracepoint pmu sdt`                         |
| Event groups      | single events handler                                             | `events` / `metrics` / `pfm-events` — three separate states                   |
| Comma-separated   | manual split                                                      | `_sequence` wrapper (events, metrics, fields, sort-keys)                      |
| `perf list <TAB>` | only event names                                                  | fallthrough `;&`: event-type keywords + event names                           |
| Command-to-run    | N/A                                                               | `perf stat/record/trace -- <TAB>` via `->command` state + `_command_names -e` |
| kwork             | not in bash                                                       | kwork subcommand: record/report/latency/timehist/top                          |

> Manually reviewed and tested.

## Install

### zinit (zi)

```zsh
zi ice lucid wait as'completion'
zi light saying121/linux-perf-completion
```

### Manual

```zsh
cp _perf /path/to/your/fpath/
# then restart shell or run compinit
```
