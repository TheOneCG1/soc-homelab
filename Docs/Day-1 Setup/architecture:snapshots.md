# Snapshot Strategy

Snapshots are used to preserve known-good states of the lab.

## Day 1 Snapshot
- Name: day1-networking-complete
- Purpose:
  - Preserve clean networking state
  - Allow rollback if future changes fail

## Usage
Snapshots are taken:
- Before major configuration changes
- After successful milestones
- Soc-server day1 snapshot made
- Windows-endpoint snapshot made
- Ubuntu-attacker snapshot made
