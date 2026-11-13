# Halum roadmap

This roadmap sets out what Halum is building, in what order, and why. It is a living document: later milestones will send us back to revise earlier ones.

Items marked **DRAFT** are temporary decisions made so that engineering can start. They will be revisited at the milestone named next to them.

## Problem statement (DRAFT, revisit at M7)

People in biomedical engineering keep starting from scratch because tools, data and know-how are scattered. Halum gives them one open place to find projects, reuse work and build on each other.

Each project has its own, narrower problem statement in its own repository. For halum-platform, see [docs/design.md](https://github.com/Halum-Ecosystem/halum-platform/blob/main/docs/design.md).

## Status

| Milestone | Status |
|---|---|
| M0. Git foundations | Done |
| M1. Hub and community basics | Done |
| M2. One-page platform design | In progress (drafts) |
| M3. Offline signal processing | Can start now, alongside M2 |
| M4. Live pipeline | Not started |
| M5. Virtual hand, the first public demo | Not started |
| M6. Real signals from the Arduino Uno | Not started |
| M7. Open the doors | Not started |

## What matters most

In priority order. Each is a concept to understand before the code that depends on it.

1. **Interfaces before implementations.** Define what a "sample" is and what a module must provide. Good interfaces let strangers contribute without understanding everything.
2. **Time.** Each device has its own clock, and combining signals is meaningless if timestamps disagree. Learn device clock vs host clock, drift and jitter.
3. **Signal fundamentals.** Sampling rate, Nyquist and aliasing, resolution, noise, filtering.
4. **Provenance.** Devices change their APIs, protocols and firmware, and some filter data in undocumented ways. Record what happened to the data before it reached us, so changes are visible rather than silent.
5. **Latency budget.** Decide the maximum delay from muscle signal to hand movement, then allot it across stages. Confirm a target figure from the literature.
6. **Failure behaviour.** Decide what happens on a disconnected electrode, dropped samples or a crashed process. Anything driving a motor needs a defined safe state.
7. **Reproducibility.** A recording is only useful with its calibration, device settings and session details.
8. **Testing without hardware.** Simulators and replay of recorded data let anyone work with no equipment.
9. **Writing decisions down.** A short decision record per major choice: problem, options, choice, why.
10. **Safety and ethics from day one.** Research and education only, no patient data in repos, human-subject work follows institutional rules. See [Safety.md](Safety.md).

## Decisions

| Decision | Status | Why it matters |
|---|---|---|
| Repository structure | Decided: hub with project repos as submodules | Projects share conventions, not code |
| Licences | Decided: Apache-2.0 code, CERN-OHL-S-2.0 hardware, CC-BY-4.0 docs | Hard to change after others contribute |
| Platform language | Suggested: Python to start | Fast iteration, strong signal libraries |
| Data model and module interfaces | DRAFT in halum-platform `docs/design.md`, revisit at M4 | Everything else depends on it |
| Timestamps and sync | DRAFT: host stamps on arrival with a monotonic clock. Evaluate Lab Streaming Layer at M4 | Time sync is hard. This should be the first decision record |
| How modules are wired | DRAFT: a config file naming one source, processors and one output | Lets people run new experiments without editing the core |
| Hand source | Open | Use an openly licensed design or model our own; check licences before publishing any STL |
| EMG front end for M6 | Open | See the M6 note on AD8232 vs MyoWare |

## Milestones

**M0. Git foundations** (done)
- Practise the branch, commit, pull request cycle on the hub.

**M1. Hub and community basics** (done)
- README around Halum's three strands, licences, contributing guide and `Safety.md`.
- First project repos created and added as submodules.

**M2. One-page platform design** (in progress)
- Before any platform code: problem statement, scope, block diagram, data model, module interfaces and failure behaviour.
- Questions to answer: What fields does every sample carry? Who assigns timestamps? How does a device describe its channels, units and upstream processing? How is a session identified?
- Temporary drafts of all of these are in halum-platform `docs/design.md`.
- Review: the design page, tested against cases it wasn't built for.

**M3. Offline signal processing** (can start now)
- In one script: generate simulated EMG, band-pass, rectify, extract the envelope, convert to a 0 to 1 grip value, and plot each stage. Then try real recordings from a public dataset such as NinaPro.
- M3 doesn't depend on M2 decisions, and what it teaches makes those decisions easier.
- Done when: you can explain why each stage exists and how its parameters change the result.

**M4. Live pipeline**
- Turn M3 into simulator, stream and processing modules using the M2 interfaces.
- Revisit every M2 draft and write the timestamps decision record.
- Done when: a module can be swapped by changing configuration only, and latency and dropped samples have been measured.

**M5. Virtual hand, the first public demo**
- An output module drives a hand on a live dashboard.
- Keep hand dimensions in one parameter file, so a printable hand stays possible later.
- Done when: someone else can run it from the README on a clean machine with no hardware.

**M6. Real signals from the Arduino Uno**
- Stage one: a potentiometer as a stand-in signal, to prove ADC, serial, stream and hand end to end.
- Stage two: an EMG amplifier module. Electrodes cannot go straight into the Uno: surface EMG is about 0.1 to 5 mV, and one ADC step is about 4.9 mV.
- **Choosing the front end:** common AD8232 breakout boards are configured for ECG, with a low-pass filter in the tens of hertz, while surface EMG energy sits mostly around 20 to 450 Hz. Check any board's schematic before buying. MyoWare's raw output, or another EMG-specific front end, is a better fit. MyoWare's default envelope output is already rectified and smoothed, so its stream description must say so.
- **Electrical safety:** with electrodes on a person, the laptop runs on battery, unplugged from mains.
- Questions to answer: What sample rate is justified? Does the serial link carry it?
- Review: wiring and firmware before connecting to a person.

**M7. Open the doors**
- Open Discord and Discussions widely once M5 runs, so newcomers have something to try. Add "good first issue" tasks such as a new simulator or filter.
- Keep to one active project until then.

## On hold until after M5

- Hospital standards: HL7, FHIR, IEEE 11073, and the European Health Data Space.
- Community moderation policy. Code and data integrity (branch protection, required reviews, CODEOWNERS for firmware, checksums on datasets) still apply from the start.
- A community registry characterising devices' hidden filtering.
- Halum's AI layer (Greg).
- A printable hand generated from the virtual hand, with build instructions.
- Streaming between machines.
- A gesture classifier as a swappable processing module.

## How we check progress

- Each milestone's "done when" is demonstrated by running it, not assumed.
- Design reviews test whether the design handles a case it wasn't built for, for example an ECG channel at a different sample rate.
- The real test of the open-source goal is M5: a person who isn't the author gets it running from the README alone.
