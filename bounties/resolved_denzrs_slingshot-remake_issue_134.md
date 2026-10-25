# Automated Bounty Resolution

- **Issue:** https://github.com/denzrs/slingshot-remake/issues/134
- **Title:** Explore PvP twists that shift player priorities
- **Reward:** $50 USDT (BEP-20)
- **Payout Address:** `0x1c088878957d52736337ec7a000d335a204e9b71`
- **Submitted By:** @Dungsky
- **Timestamp:** 2026-10-25T17:59:24.195Z

## Solution Summary
Designed a comprehensive design document detailing three new physics-driven PvP variants (Bounty, Orbital Relay, and Gravity Well Control) that introduce alternative objectives and scoring rules centered around Slingshot's gravity mechanics.

## Solution Code / Content
```
# PvP Twists & Variants Design Document: Shifting Player Priorities in Slingshot

## Overview
To elevate Slingshot beyond standard elimination deathmatches, this document explores new gameplay variants that overlay strategic objectives onto the core mechanics (Classic, Event Horizon, and Solar System). By leveraging gravity-based projectile physics, these modes force players to balance elimination threats with high-value tactical positioning and shot trajectories.

---

## Variant 1: Bounty (King of the Hunt)

### Concept
A dynamic target system where the player leading in score or surviving the longest is marked as the "Bounty." Eliminating the bounty grants massive bonus points, resetting or shifting the bounty target to another contender.

### Gravity-Centric Mechanics
- **Orbital Shielding:** The active Bounty gains a minor gravitational pull (a micro-gravity well) that deflects incoming low-velocity projectiles slightly, making direct hits harder and requiring indirect slingshot banked shots.
- **Risk/Reward Trajectory:** Bounties generate pulsating gravity pulses every few turns, pulling nearby floating debris or altering the curvature of projectiles passing near them.

### Scoring Rules
- Standard elimination: 100 pts.
- Eliminating the Bounty: 500 pts + bonus multiplier for remaining turn time.
- Surviving a round as the Bounty: +50 pts per turn survived.

---

## Variant 2: Orbital Relay (Control Points in Motion)

### Concept
Capture points (Relays) constantly orbit celestial bodies across the map. Players must land their projectiles or position their gravity trails within the relay zone to capture it.

### Gravity-Centric Mechanics
- **Keplerian Capture:** Because relays follow elliptical orbits governed by the map's gravity fields, players must calculate lead times and gravitational slingshots not just to hit opponents, but to intersect moving capture zones.
- **Anchor Shots:** Players can "park" a spent projectile inside a relay's gravitational orbit to contest or hold it for subsequent turns, creating physical barriers.

### Scoring Rules
- Holding a relay at the end of a round: 200 pts per relay.
- Intercepting an opponent's projectile inside the relay zone: +100 interruption bonus.

---

## Variant 3: Gravity Well Control (Resource Harvesting)

### Concept
An unstable core spawns at the center of the map. Players shoot high-density energy nodes into the well to harvest points, but the gravitational pull grows exponentially heavier the more mass is accumulated.

### Gravity-Centric Mechanics
- **Black Hole Mechanics:** Every successful shot trapped in the central well increases its mass. Shots fired later in the round suffer extreme gravitational lensing, curving wildly.
- **Event Horizon Risk:** If a player's shot falls too deep into the central well without harvesting, it is consumed, penalizing the shooter and feeding energy back to opponents.

### Scoring Rules
- Successful harvest deposit: 50 pts per unit of mass.
- Causing an opponent's shot to fall into the Event Horizon: Steals 50% of their accumulated round score.
```
