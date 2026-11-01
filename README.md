# Research artifact: What Else Gets Repaired? Mining and Auditing Cross-File Repair after AI-Marked Commits

All files work when kept together in one folder. Install with `pip install -r requirements.txt`.

## Data and results
| File | Contents |
|---|---|
| table_d1.csv | Repository-level data: 45 repositories, matched sets (n), R14 rate for marked and control commits (%), difference (pp), repository type (ai_repo, post hoc) |
| repositories.csv | All 77 repositories chosen in advance, whether each entered the analysis, and its results |
| sensitivity_results.csv | Main result, sensitivity analyses S1-S7, post hoc checks and secondary outcomes |
| simulation_summary.csv, noise_curve_summary.csv | Simulation results (Table 3, Appendix Table A5, Fig. 2) |
| prespecification_record.csv | Which analyses were pre-specified and which were post hoc |

## Rules and protocols
| File | Contents |
|---|---|
| marker_rules.md | AI-assistance marker detection rules and outcome keywords |
| validation_protocol.md | Protocol for validating the R14 proxy and the markers |

## Scripts
| Script | Reproduces | Command |
|---|---|---|
| reanalysis.py | Table 2, prediction interval, meta-regression | `python reanalysis.py` |
| fragility_exact.py | Fragility indices (2, 8, 6) | `python fragility_exact.py` |
| bias_analysis.py | Section 7 bias analysis | `python bias_analysis.py` |
| simulation.py | Table 3 (scenario S = 0-5; paper names Sim0-Sim5) | `python simulation.py 2000 S` |
| simulation.py | Volatility sensitivity | `python simulation.py 1000 S 0.5` or `2.0` (S = 0, 2) |
| sim_noise_curve.py | Fig. 2 data | `python sim_noise_curve.py DQ SEED` with SEED = 100 + DQ (DQ = 0..5); `python sim_noise_curve.py 3 777 post` |
| fig_noise.py, fig_metareg.py | Figs. 2 and 1 | `python fig_noise.py`, `python fig_metareg.py` |
| sample_events.py, analyse_labels.py, marker_audit.py | Validation toolkit | see each file's header |

**Seeds.** Simulation scenarios use the CRC32 hash of the scenario name (plus 1000 x 10 x volatility SD), so results are identical across runs. Bootstrap seeds are fixed in each script (20261020 for the re-analysis and bias analysis). The matching seed was 20261020.
