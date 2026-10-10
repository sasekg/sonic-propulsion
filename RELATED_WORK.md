# Related Work and Visual References

This page collects research and visual references related to the [Sonic Propulsion experiment](README.md): non-contact horizontal steering of a lightweight object using **16 independent ceiling speakers**, timed audible-frequency pulses, complex room interference, and camera feedback.

> **Scope distinction:** most published demonstrations below use ultrasonic transducers at short distances, or mechanical excitation of a plate. They do **not** establish that a 20 Hz–20 kHz array of conventional loudspeakers, 10+ feet above a floating target, can steer it. Their value is in demonstrating mechanisms and experimental methods.

## 1. Single-sided acoustic levitation and manipulation

**Marzo et al. (2015), “Holographic acoustic elements for manipulation of levitated objects,” Nature Communications.**

- [Open-access article and figures](https://www.nature.com/articles/ncomms9661)
- [Full text and supplementary videos](https://pmc.ncbi.nlm.nih.gov/articles/PMC4627579/)
- **Visual:** [Figure 2 — photographs of levitated polystyrene particles](https://www.nature.com/articles/ncomms9661#Fig2)
- **Relevance:** independently phased emitters can create nontrivial acoustic traps, including translation and rotation. The experiment uses **40 kHz ultrasonic transducers** and millimeter-scale particles, not room-scale audible speakers.

## 2. Acoustic holograms and manipulation at a water–air interface

**Cox et al. (2019), “Acoustic Hologram Enhanced Phased Arrays for Ultrasonic Particle Manipulation,” Physical Review Applied.**

- [Research article and figure gallery](https://doi.org/10.1103/PhysRevApplied.12.064055)
- **Visual:** figure gallery in the paper includes the array/hologram arrangement and manipulation demonstrations.
- **Relevance:** combines phased control with structured acoustic fields, including motion of a **phase surfer at a water–air interface**. Particularly relevant to a floating target, but implemented with ultrasound and different hardware.

**Melde et al. (2016), “Holograms for acoustics,” Nature.**

- [Article and figures](https://www.nature.com/articles/nature19755)
- **Visual:** Figures 2 and 3 show particle assembly and phase-gradient surfers.
- **Relevance:** demonstrates the ability of engineered acoustic fields to shape matter and induce controlled motion. Uses acoustic holograms rather than this project's adaptive audible speaker array.

## 3. Chladni patterns and learned vibration control

**Zhou et al. (2016), “Controlling the motion of multiple objects on a Chladni plate,” Nature Communications.**

- [Open-access paper with experimental images](https://www.nature.com/articles/ncomms12764)
- [Full text and figure references](https://pmc.ncbi.nlm.nih.gov/articles/PMC5023966/)
- **Visual:** photographs and diagrams of objects on a vibrating plate, showing controlled motion.
- **Relevance:** especially close to the project's *learning control from complicated dynamics* idea. The authors model and control motion that can appear irregular. **Difference:** the plate is directly actuated; our speakers remain physically disconnected from the target and support.

**Tuan et al. (2015), “Exploring the resonant vibration of thin plates,” Journal of the Acoustical Society of America.**

- [Article abstract](https://pubmed.ncbi.nlm.nih.gov/25920861/)
- **Visual theme:** classic sand-on-plate Chladni nodal patterns.
- **Relevance:** supports the intuition that resonance and boundaries create intricate spatial patterns, but nodal patterns alone do not prove directional propulsion.

## 4. Acoustic tweezers and array resolution

**“Holographic acoustic tweezers” (2018).**

- [Open-access paper with images](https://pmc.ncbi.nlm.nih.gov/articles/PMC6320506/)
- **Relevance:** demonstrates individually manipulated particles using a 40 kHz phased-array system, and discusses the importance of emitter spacing and phase resolution. Highlights the limitations of a sparse 5-foot-spaced array at high audible frequencies.

**“Large-scale airborne holographic acoustic tweezers for synthesizing acoustic fields and particle manipulation” (2025).**

- [Research abstract](https://pubmed.ncbi.nlm.nih.gov/40961534/)
- **Relevance:** a much denser 2,304-element, 40 kHz system demonstrates highly controlled trajectories. It is a useful comparison for the number of channels, timing precision and attainable manipulation scale, not direct evidence for the proposed 16-speaker experiment.

## Visual concepts discussed in the originating chat

The earlier conversation included illustrative image-search results and generated schematics, **not reusable, licensed image files with stable source URLs**. To avoid attributing or copying an unverified image, the following links point to relevant, published figure collections or visual-search references. They preserve the subjects of the original illustrations.

| Chat visual | Visual reference | What it illustrates |
| --- | --- | --- |
| Chladni plate / cymatic sand patterns | [Zhou et al., figures](https://www.nature.com/articles/ncomms12764) | Nodes, antinodes and particle motion |
| Acoustic levitation of lightweight beads | [Marzo et al., Figure 2](https://www.nature.com/articles/ncomms9661#Fig2) | Non-contact manipulation in air |
| Small floating sail / sonic sail | [Image search: miniature floating sail](https://www.google.com/search?tbm=isch&q=miniature+floating+sail+model) | Proposed target geometry, **not** a validated acoustic propulsor |
| Water ripples / surface waves | [Image search: acoustic water surface waves](https://www.google.com/search?tbm=isch&q=acoustic+water+surface+waves+experiment) | Potential medium response |
| Lightweight floating disk | [Image search: lightweight floating disk on water](https://www.google.com/search?tbm=isch&q=lightweight+floating+disk+on+water+experiment) | Low-drag test target |
| Four-stage pulse-pattern schematic | [Project README](README.md) | Proposed control sequence; schematic from chat was illustrative, not measured |
| 4 × 4 speaker array schematic | [Project README](README.md) | Proposed geometry; not a simulation |

### Selected article figures (click to view)

[![Photographs of single-sided acoustic levitation — figure preview from Nature Communications](https://media.springernature.com/full/springer-static/image/art%3A10.1038%2Fncomms9661/MediaObjects/41467_2015_BFncomms9661_Fig2_HTML.jpg)](https://www.nature.com/articles/ncomms9661#Fig2)

*Marzo et al. (2015), Figure 2. External image from publisher; follow link for attribution, license and context. If the preview does not load, use the linked figure page.*

## What is new about the proposed experiment?

1. **Audible range:** 20 Hz–20 kHz rather than the 40 kHz ultrasound used by many acoustic tweezers.
2. **Long standoff:** at least 10 feet between ceiling speakers and object.
3. **Sparse, conventional speakers:** 16 independently driven sources at 5-foot spacing.
4. **Time-dependent search:** optimize **pulse sequences**, not only stationary traps or beam patterns.
5. **Adaptive closed loop:** a camera measures displacement, and a controller learns which multichannel patterns produce repeatable, commanded motion.
6. **Target/medium co-design:** the object may float, carry a sonic sail, or have tuned resonant features.

These are **experimental design differences**, not claims of novelty against all existing literature. In particular, acoustic streaming, acoustic radiation forces, surface-wave drift and nonlinear rectification must be distinguished experimentally.

## Research questions for the first trials

- Does any bounded, repeatable pulse sequence create displacement distinguishable from ambient drift?
- Is displacement caused by direct acoustic radiation pressure, induced air flow, water surface motion, or target resonance?
- Does reversing the sail orientation reverse the motion?
- Do learned pulse sequences transfer to new starting locations, object orientations and target positions?
- Can the controller command **both directions** along an axis, then steer in two dimensions?

## Image use and attribution

This page **links to** publisher figures rather than downloading or redistributing the earlier chat's search images. Article images remain subject to their stated licenses and attribution requirements. The external figure preview above is hotlinked to its publisher and may change; the article link is the durable reference.
