# TrustGraph-V2X
Trust-Aware Spatio-Temporal Graph Learning for Predictive Handover and RSU Load Balancing in 5G-V2X Networks (final-year B.Tech ECE major project).

## Status (work in progress)
- Verified: SUMO + Veins + OMNeT++ + INET + Simu5G connect over TraCI and run the Simu5G `nr/cars` toy example for ~45 s of simulated time.
- Open issue: the run aborts at t=45.9 s with an OMNeT++ "SubmoduleIterator: Submodule insertion/deletion detected" error (see logs/run1.log).
- Not done yet: NITK Surathkal scenario, dataset extraction, GNN+GRU model, predictive handover evaluation.
- The toy example is an integration test only, not NITK results.

## Tested environment (Docker, linux/amd64)
| Component | Version |
|---|---|
| OMNeT++ | 6.5.0 |
| INET | 4.6.0 |
| Simu5G | 1.5.0 |
| Veins | 5.3.1 (+ veins_inet) |
| SUMO | 1.19.0 (Veins 5.3.1 accepts TraCI API 15-21 only; SUMO 1.25 reports 22 and is rejected) |

## Fixes applied
1. SUMO 1.19.0 installed via `pip install --target /work/sumo119 eclipse-sumo==1.19.0`, and the launcher restarted with:
   `veins_launchd -k -d -v -c /work/sumo119/sumo/bin/sumo`
2. In `simulations/nr/cars/omnetpp.ini`, `dynamicCellAssociation` moved from `nrPhy` to `rrc.nrHandoverController` (the original path had no effect). Original saved as `configs/toy_cars/omnetpp.ini.orig`

cd ~/TrustGraph-Docker/trustgraph-v2x && cat > README.md <<'EOF'
# TrustGraph-V2X
Trust-Aware Spatio-Temporal Graph Learning for Predictive Handover and RSU Load Balancing in 5G-V2X Networks (final-year B.Tech ECE major project).

## Status (work in progress)
- Verified: SUMO + Veins + OMNeT++ + INET + Simu5G connect over TraCI and run the Simu5G nr/cars toy example for about 45 s of simulated time.
- Open issue: the run aborts at t=45.9 s with an OMNeT++ SubmoduleIterator insertion/deletion error (see logs/run1.log).
- Not done yet: NITK Surathkal scenario, dataset extraction, GNN+GRU model, predictive handover evaluation.
- The toy example is an integration test only, not NITK results.

## Tested environment (Docker, linux/amd64)
- OMNeT++ 6.5.0, INET 4.6.0, Simu5G 1.5.0, Veins 5.3.1 (+ veins_inet)
- SUMO 1.19.0 (Veins 5.3.1 accepts TraCI API 15-21 only; SUMO 1.25 reports 22 and is rejected)

## Fixes applied
1. SUMO 1.19.0 installed with: pip install --target /work/sumo119 eclipse-sumo==1.19.0
   Launcher restarted with: veins_launchd -k -d -v -c /work/sumo119/sumo/bin/sumo
2. In simulations/nr/cars/omnetpp.ini, dynamicCellAssociation moved from nrPhy to rrc.nrHandoverController (the original path had no effect). Original saved as configs/toy_cars/omnetpp.ini.orig

## Layout
- configs/: simulation configs
- scenarios/nitk/: NITK SUMO network and RSU files (to be added, originals untouched)
- scripts/: data extraction, training, evaluation
- logs/: run logs
- docs/: report and slides
