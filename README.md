# Sonic Propulsion

📚 [Related work and visual references](RELATED_WORK.md)

**Experimental research concept: remote, closed-loop steering of lightweight objects using timed acoustic interference.**

## Research question

Can an adaptive controller discover repeatable sequences of acoustic pulses that move a lightweight object in commanded horizontal directions, even when the room's acoustic interference field is too complex to model accurately?

This is a proposal for an experiment, **not** a demonstrated propulsion technology.

## Physical setup

- **Transmitters:** up to 16 independently driven, conventional airborne loudspeakers, arranged in a 4 × 4 square grid on a ceiling.
- **Spacing:** 5 feet between adjacent speaker centers, giving a 15 × 15 ft span between outermost speaker centers.
- **Separation:** at least 10 feet vertically between speakers and the target (depending on speaker mounting and target height).
- **Signal band:** 20 Hz–20 kHz, subject to each speaker's actual usable response and safe operating limits.
- **No contact:** speakers are not physically connected to the target, its support, or its medium.
- **Target:** initially an arbitrarily lightweight, camera-trackable object; possible configurations include a floating disk on still water, a lightweight object with a flexible membrane or *sonic sail*, or an object resting on a resonant surface.
- **Receiver/feedback:** overhead or side-view camera tracking position and, where practical, orientation and velocity.

Conceptual ceiling plan (speaker centers, top view):

```text
S01 ---- S02 ---- S03 ---- S04
 |        |        |        |
S05 ---- S06 ---- S07 ---- S08
 |        |        |        |
S09 ---- S10 ---- S11 ---- S12
 |        |        |        |
S13 ---- S14 ---- S15 ---- S16

Adjacent spacing: 5 ft
Object: >=10 ft below array
```

## Hypothesis

A time-varying combination of speaker signals may produce a small *net* horizontal displacement via acoustic radiation forces, acoustic streaming, sound-excited motion of a supporting medium, or asymmetric mechanical response of a sail or resonator. A feedback-driven agent may learn useful pulse patterns empirically instead of relying on a complete field model.

**Important distinction:** linear interference produces changing pressure and particle velocity, but does not by itself guarantee net force or locomotion. Successful steering requires a mechanism for momentum transfer and rectification. This experiment seeks to identify whether such mechanisms produce *repeatable, controllable* displacement at the proposed scale.

## Signals and control parameters

For channel `i`, a basic gated sinusoid is

```text
s_i(t) = A_i(t) · sin(2π f_i t + φ_i(t))
```

where the controller may set:

- Frequency, amplitude and relative phase
- Start time and inter-speaker delay
- Burst duration, repetition interval and number of pulses
- Attack/release envelope and pauses
- Multitone or frequency-swept bursts (within safe speaker limits)

A **policy** produces a sequence of multichannel bursts, observes the target, then chooses the next burst. Pulse sequences need not resemble a static beam or a single focal point. The controller is explicitly permitted to exploit reflections, room modes, sidelobes, transients, and nonlinear target/medium responses.

## Why pulse sequences?

A pulse can excite a short-lived sound field, fluid response, or object resonance; a subsequent pulse may interact with the remaining motion. A sequence of apparently opposing stimuli could still produce net displacement because of inertia, damping, friction, threshold effects, or asymmetry. This is a testable possibility, **not** an assumption.

The goal is not merely to discover pulses that shake the target. The goal is to find reproducible cause-and-effect patterns that can be combined into commanded 2D motion.

## Candidate targets / couplings

| Target configuration | Possible coupling | Main difficulty |
| --- | --- | --- |
| Very light disk floating on still water | Radiation force, acoustic streaming, induced surface-wave drift | Water motion and background drift |
| Floating disk with vertical or angled lightweight sail | Radiation pressure, streaming and asymmetric drag | Weak airborne forcing at distance |
| Flexible diaphragm or tuned cavity on the target | Resonant motion with nonlinear rectification | Converting oscillation into directed translation |
| Lightweight object on a resonant surface | Airborne excitation of surface modes, slip or rocking | Weak coupling and irregular contact forces |

A **sonic sail** is a proposed test article, not an established sound-to-thrust amplifier. Its geometry, angle, stiffness and mass are experimental variables.

## Acoustic constraints

At room temperature, `λ ≈ 343/f` meters. Representative wavelengths are approximately 3.43 m at 100 Hz, 34 cm at 1 kHz, and 1.7 cm at 20 kHz. With 1.52 m (5 ft) speaker spacing, high-frequency phased operation has substantial spatial aliasing / grating lobes, and the room adds reflections. Speakers may also be poorly matched at high frequencies.

Therefore, rather than promise a single clean steerable focus, this project investigates whether **complicated interference patterns themselves** can become useful control actions. This does not imply that usable acoustic force will be large enough: force magnitude and repeatability must be measured.

## Proposed experiment

### Phase 0 — Establish a measurable baseline

1. Map speaker positions, polarity, frequency response and latency; calibrate per-channel playback and synchronized onset.
2. Record ambient airflow, water drift, vibration, temperature, and camera-tracking noise with speakers off.
3. Place a lightweight floating marker in a sheltered shallow tank, well away from walls; record its unforced drift.
4. Establish safe sound-pressure and duty-cycle limits and an emergency stop.

### Phase 1 — Single-channel and simple-pattern characterization

1. Test one speaker at a time across a limited set of frequencies, amplitudes and burst envelopes.
2. Repeat each trial from the same initial position and after water has settled.
3. Compare a plain floating target against equal-mass targets with differently oriented sails or membranes.
4. Test simultaneous and phase-offset speaker pairs. Record direction, displacement, velocity and scatter.

### Phase 2 — Pulse-sequence search

1. Specify a command: e.g., move 5 mm along +X within a fixed trial duration.
2. Generate bounded, reproducible 16-channel pulse sequences (seeded random search is a valid starting point).
3. Track the object continuously and log every waveform/control setting.
4. Score each candidate by target-directed progress, consistency across resets, unwanted lateral motion and energy.
5. Re-test promising sequences over independent trials, rotated target orientations and different start positions.

### Phase 3 — Closed-loop 2D steering

Estimate position and velocity after each burst; use the observed state and a specified destination to select the next action. Evaluate reachability, stopping accuracy and performance on paths that were **not** used in training. Compare against random policies and simple single-speaker heuristics.

## Example objective

For target position `p_goal`, initial position `p_0`, and final position `p_T`, minimize

```text
J = w_goal · ||p_T - p_goal||²
  + w_energy · total_signal_energy
  + w_cross · unintended_cross_track_motion
  + w_var · variation_across_repeated_trials
```

Add limits on maximum channel output, exposure, burst duty cycle and test duration. For a first test, use signed progress toward the goal in addition to final target error; otherwise a candidate that starts closer to the goal may be misleading.

## Evidence and controls

A successful result requires **repeated, target-directed motion beyond baseline drift**, demonstrated on held-out trials. Controls should include:

- Speakers off; and speakers on with randomized/non-optimized sequences at matched power
- Object without sail; equal-mass control object; sail reversed or rotated
- Repeated start positions, orientations and water-settling intervals
- Airflow shielding and measurement; elimination of mechanical speaker-to-tank coupling
- Camera calibration and blinded/offline evaluation of trajectories when possible

Measure effect sizes and distributions, not just the best video. Report null results. Distinguish acoustic-radiation effects from streaming or induced surface motion whenever possible; finding a useful mechanism is valuable even if it differs from the initial hypothesis.

## Suggested data record

Each trial should capture:

```text
trial_id, timestamp, target_design, mass, medium,
speaker_layout, calibration_id, random_seed,
frequency/amplitude/phase/envelope/delay per channel and pulse,
initial_position, target_position, tracked_trajectory,
duration, ambient_conditions, outcome, safety_limits
```

Store raw tracking trajectories, commanded waveforms and enough configuration to replay each trial.

## Safety

Sixteen loudspeakers can produce hazardous sound levels, particularly near resonance or with combined output. The full audible band includes frequencies that may be uncomfortable or inaudible to some listeners while still presenting risks. Begin at conservative levels, use calibrated sound-pressure measurements and remote operation, keep people and animals away from test exposure, and use hardware/software output limits and an emergency stop. Protect electrical equipment from water. Avoid generating extreme low-frequency or high-frequency output without equipment ratings and an exposure assessment.

## Status

**Concept / experimental specification only.** No propulsion, steering precision, useful power threshold or successful result is claimed. Hardware choices, control software, raw data and reproducible results can be added as the project develops.

## Initial milestone

Demonstrate a statistically distinguishable, repeatable horizontal displacement in one commanded direction using non-contact airborne sound, then demonstrate both +X and −X, followed by arbitrary 2D steering.
