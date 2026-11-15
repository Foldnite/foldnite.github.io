# Foldnite Arctic — MAS “Snezhinka”

**A scientific game-world concept based on the Arctic research station MAS “Snezhinka”.** The public page is a VK Play-oriented product presentation; this README does not assert that a live VK Play listing or downloadable release is available.

![](https://foldnite.github.io/arctic/assets/img/mas-sn2.jpg)

Foldnite combines **STEM + Foldit-inspired scientific problem-solving + Fortnite-inspired worlds (UEFN) + quantum computing**. Players explore the station, operate virtual equipment, travel across the Arctic, and solve team missions.

> This is a planning document, not a vendor quotation, approved funding commitment, or proof that every proposed feature is already implemented.

## 1. Product scope

The world is planned around seven station domains: 
1. energy; 
2. climate and environment;
3. biology and medicine;
4. robotics and transport; 
5. materials and engineering; 
6. connectivity and control; 
7. living and life support.

![](https://foldnite.github.io/arctic/assets/img/mas-sn1.jpg)

Initial budgeting assumptions:

| Item | Scope |
|---|---:|
| World footprint | 4 × 4 km (16 km²) |
| Detailed station / expedition area | ~2–3 km² |
| Main missions | 8 |
| Additional missions / contracts | 12 |
| Initial languages | English and Russian |
| Cooperative session | Up to 4 players |
| Camera | First- and third-person |
| VR | Optional PC-VR / OpenXR |

These are planning assumptions, not measurements of a completed build.

## 2. Technology architecture

- **STEM:** biology, chemistry, physics, materials, robotics, energy, climate, and engineering missions.
- **Fortnite / UEFN:** creator-oriented interactive worlds, missions, multiplayer patterns, and real-time effects. UEFN content is a separate Fortnite publishing target; it does not automatically become a standalone VK Play build.
- **Foldit:** inspiration for transforming scientific problems into collaborative puzzles. Foldnite is independent and does not claim to be the official Foldit product or use its code without permission.
- **Quantum computing:** optional backend for selected suitable algorithms and experiments; classical CPU/GPU/HPC remains the baseline.
- **Cloud gaming:** remote rendering and streaming to browsers/thin clients to reduce the need for high-end user devices.

**Runtime distinction:** the current Arctic production baseline is UNIGINE 2.22. For this runtime, investigate **UNIGINE WebStream / WebRTC**. **Epic Pixel Streaming** is an option for a separately packaged Unreal Engine application. **UEFN** is a Fortnite creation/publishing environment. Do not describe these as the same pipeline.

UNIGINE SDK 2.22 was released on 10 September 2026 and includes Sequencer, Animation Graph and procedural-pose improvements, sensor-simulation features, and AI/MCP tooling. Confirm the commercial edition, runtime redistribution rights, WebStream availability, and licence terms before procurement.

References:
- [UNIGINE 2.22](https://unigine.com/ru/news/2026/unigine-sdk-2-22-release)
- [UNIGINE developer documentation](https://developer.unigine.com/)
- [UNIGINE licensing](https://unigine.com/get-unigine/)
- [UEFN documentation](https://dev.epicgames.com/documentation/fortnite/unreal-editor-for-fortnite)
- [Epic Pixel Streaming](https://dev.epicgames.com/documentation/unreal-engine/pixel-streaming-in-unreal-engine)

### Foldnite mission architecture: VBMA + SOS/UAG

**Foldnite is a platform for creating scientific game worlds in which spatial assembly, structured scientific objects, computation and result verification are connected in one system of interactive missions.** MAS “Snezhinka” is a concrete Arctic example, not the only target world.

The layers have distinct responsibilities:

- **VBMA (Voxel–Block–Molecular Architecture):** reusable block-based spaces and terrain, plus typed node-link representations for molecular structures, equipment, mechanisms and scientific relationships.
- **SOS / SKG / SEM:** canonical scientific object types and states, knowledge relationships, operations, agents, experiments, workflows, measurements and provenance.
- **UAG:** the engine-neutral assembly package that references semantic objects, world nodes, interactions, constraints, source hashes and runtime requirements.
- **Mission Factory / Mission Production Compiler:** transform an approved scientific or engineering brief into a Mission Contract, Gameplay IR and bounded materialisation plan. Raw prompts do not directly become unrestricted editor operations.
- **UNIGINE 2:** the Arctic world’s visual and physics-simulation runtime. UEFN/Fortnite, Unity, Web, VR and standalone builds remain separate runtime targets requiring explicit adapters and qualification.
- **Scientific MCP / QSIS:** route authorised computation through typed, versioned capabilities and reproducible job records.
- **Validation Fabric:** keeps simulation, AI proposals and raw computation separate from independent claim-specific validation.
- **Evidence:** binds accepted results to exact inputs, revisions, tool/model versions, sources and validator records, and can return validated knowledge to the scientific graph.

**Construction-brick / LEGO-like modular composition is a long-standing part of Foldnite’s architecture and visual language.** It is not a claim of official LEGO affiliation or permission to use LEGO-owned assets; asset-level rights remain separately governed.

### Spatial capture and geospatial provenance

The project owner reports that the Arctic world’s source workflow used medium- and high-resolution mapping UAVs, satellite-derived elevation products and satellite imagery, GNSS/GLONASS RTK georeferencing, professional panoramic/3D-VR capture, an underwater ROV, and photogrammetric/geodetic processing. The owner reports that the combined material enabled photorealistic, centimetre-scale scene detail. The capture modalities and submitted reference photographs are recorded in the partnership evidence register. For engineering use, any quantitative accuracy claim must be tied to source datasets, coordinate and vertical datums, calibration/ground-control residuals, processing versions and exact dataset/build hashes.

The current VBMA/SOS/UAG integration is a governed design/standardisation path; the existence of a document or schema does not by itself mean the world compiler, runtime adapters or scientific validation path are fully deployed.


### Educational alignment with SiriusPlay: MAS “Snezhinka” as a complementary Arctic science world

The public [World of Knowledge of Sirius](https://siriusplay.ru/) page describes it as a joint project of the Federal Territory of Sirius and Lesta Games. It says that a child develops through play, meaning, choice and experience rather than grades and templates. The page sets out four main principles and five elements of the participant experience. The mapping below uses the wording published on that page.

**Compatibility assessment:** the Foldnite / MAS “Snezhinka” concept has no inherent conflict with these principles. It can serve as a specialised Arctic science-and-engineering world within a broader SiriusPlay learning journey, provided learner agency, accessibility, mentor involvement and the distinction between game progress and scientific evidence are preserved. This is a Foldnite design proposal, not a SiriusPlay approval, accreditation, partnership announcement or proof of a live integration.

| SiriusPlay principle | Proposed application in MAS “Snezhinka” | Required guardrail |
|---|---|---|
| **Accessibility** | Offer beginner and advanced mission paths, clear onboarding, non-VR participation and a route suitable for supervised classroom use. | The current Arctic page lists Windows 11, Core i7-12700K, 32 GB RAM and RTX 3080 as minimum PC specifications. A high-spec PC-only route would not satisfy an “accessible to everyone” objective. Browser, cloud or institution-provided access remains a target until it is tested and deployed; VR must remain optional. |
| **Thinking from first causes** | Make cause-and-effect relationships visible across station energy, weather, transport, communications, biology and life-support systems. Ask learners why a system behaves as it does, not only which button to press. | Show assumptions, units and simplifications. A game model must not be presented as a measured property of the real station unless source data supports that claim. |
| **Social learning** | Use cooperative roles such as researcher, engineer, analyst and coordinator; make teams compare hypotheses, share findings and explain decisions. | Avoid making individual leaderboards or speed the main definition of success. Support mentor-led and small-group modes where live multiplayer is not available or qualified. |
| **Engagement through play** | Use exploration, meaningful objectives, discovery, feedback and visible consequences to sustain effort. | Rewards and game scores measure game progression only. They must not override scientific correctness, learner wellbeing or the mission’s declared acceptance criteria. |
| **Belonging to something larger** | Place missions in the context of Arctic research, autonomous stations, climate, energy, robotics and international scientific work. | Distinguish real-world context from fictionalised or simulated events. Do not claim that player actions contribute to live station operations or real research unless a specific authorised workflow proves it. |
| **Responsibility through consequences** | Let learners observe how decisions affect simulated energy reserves, logistics, communications, environmental conditions and life-support margins. | Consequences must be clearly labelled as simulated where appropriate. The educational client must not control real station equipment or be mistaken for an operational decision-support system. |
| **Independent choice of path** | Let each learner choose a role, task order, difficulty and permitted problem-solving route within a mission. Offer alternative approaches to the same learning objective. | Mission Inception and Mission Contracts define scientific scope, safe actions, permitted tools and evidence requirements; they should not prescribe one compulsory learner journey when several safe routes are possible. |
| **Living, adaptive environment** | Let learner ideas, annotations, world-building proposals and mission variants become candidates for future content. Provide visible ways to suggest and discuss improvements. | Community suggestions enter a review pipeline. Mentor, moderation, rights, privacy, safety and scientific review are required before publication; user-generated content is not silently promoted into the canonical scientific world. |
| **Experience rather than memorisation** | Make learning experiential: explore, build, manipulate, simulate, compare, discuss and finish with a structured debrief. Ask learners to explain what they changed and why. | Do not reduce the experience to quizzes or recall tests. A scientific Evidence record is not a learner grade and must not be used as a proxy for a child’s talent or overall educational progress. |

#### Keep learner progress and scientific Evidence separate

Foldnite’s governance can reinforce SiriusPlay’s learner-centred approach if two different kinds of status remain distinct:

- **Learning experience:** the learner’s chosen path, role, collaboration, reflection, mentor feedback and personal progress.
- **Scientific result:** whether a specific claim or candidate satisfies a mission-bound protocol and an appropriate claim-specific validation process.

A Mission Contract may constrain scientific inputs, tools, safety and claim scope without forcing a single pedagogical route. Likewise, ACCEPTED, REJECTED or INDETERMINATE scientific outcomes describe the submitted result under its protocol; they are not grades for the learner. The mission should reward curiosity, explanation, teamwork and responsible experimentation, not merely a high score or a favourable scientific outcome.

#### Proposed SiriusPlay integration boundary

The most compatible model is **SiriusPlay as the broader educational entry point and learning journey; Foldnite / MAS “Snezhinka” as a specialised interactive Arctic science world**. This is a product-integration proposal, not a proposal to replace SiriusPlay’s world, merge its game engine with UNIGINE, or require SiriusPlay to adopt qFoldIT’s internal schemas.

1. **Discover and prepare in SiriusPlay:** an educator or learner selects an approved Arctic science experience, age/skill level and learning objective.
2. **Launch the Foldnite world through an authorised hand-off:** a link, launch integration or other mechanism agreed with the SiriusPlay technical owner opens the appropriate Snezhinka experience. The exact mechanism (including any SSO, embedding or SDK) must be confirmed; no public SiriusPlay API or authentication contract is assumed here.
3. **Explore and solve in Foldnite:** UNIGINE 2 presents the Arctic environment; VBMA organises spatial and node-link views; SOS/SKG/SEM and the approved Mission Contract preserve scientific meaning and action boundaries.
4. **Return a minimal learning summary:** with the required permissions, Foldnite may return a mission identifier/version, completion state, learner reflection and mentor-facing summary. A scientific validation status or Evidence reference is included only when that result actually exists and is authorised for sharing. Avoid exporting raw behavioural telemetry or unnecessary personal data.
5. **Continue the learner journey in SiriusPlay:** the result can inform the next optional activity, discussion or mentor review without turning scientific acceptance into a student ranking.

Before implementation, the parties would need to agree the content catalogue and launch interface, identity and age/consent model, permitted data exchange, mentor/moderation responsibilities, accessibility targets, service support, content ownership and acceptance process. Public SiriusPlay materials describe its educational principles and product positioning, but do not establish that these integration interfaces are available to Foldnite.

#### Conditions to close before calling this an integration

- **Accessibility:** prove at least one non-VR, lower-friction access route on the devices actually used by the target learners. Cloud/WebStream is a proposed option, not a verified deployed substitute for the current high PC requirements.
- **Pedagogy:** co-design age-appropriate mission variants with educators and mentors. Keep learner choice and reflection visible; do not make opaque AI profiling or automated difficulty assignment the sole determinant of a learner’s path.
- **Child safety and data:** agree age-appropriate supervision, consent, data minimisation, retention, moderation and escalation rules before any student pilot.
- **Scientific and operational safety:** label simulations, AI proposals and computed outputs accurately; keep the educational world isolated from real station controls and operational systems.
- **Rights and licensing:** obtain written permission for the relevant SiriusPlay/Lesta names, logos, materials and any platform integration. The Foldnite repository now carries a Restricted Proprietary License dated 15 November 2026; external use, hosting, modification or distribution of Foldnite-owned material requires the specific written authorisation or agreement. Third-party assets and datasets retain their own licence requirements.
- **Partner status:** until a written agreement and technical acceptance exist, describe the relationship as “proposed SiriusPlay integration” or “designed for potential compatibility”, not as an official SiriusPlay product, approved curriculum or existing partnership.

Primary reference: [World of Knowledge of Sirius — official principles](https://siriusplay.ru/). Related public project context: [Sirius innovation and technology centre resident directory](https://intc.sirius.ru/residents/).

## 3. Cloud-first gaming

A remote GPU session renders the world and streams video/audio to a browser or lightweight client. The device still decodes the stream and sends input, so latency, packet loss, codec support, and network quality matter.

~~~text
Browser / Thin Client / PC
        | WebRTC video/audio + player input
        v
Session Gateway / Signalling / TURN
        v
Cloud GPU Render Session (UNIGINE)
        +-- game simulation, physics, weather
        +-- Mission API / Station Twin
        +-- AI and Scientific MCP adapters
        +-- optional asynchronous QuantumCompute adapter
        v
Workflow / validation / saved mission results
~~~

Keep render sessions and heavy scientific batch jobs in separate resource pools and priority queues.

| Workload | Execution |
|---|---|
| Cloud rendering | Dedicated GPU render-session pool |
| Native PC rendering | Player’s PC when local mode is selected |
| Vehicle physics / gameplay | Game runtime with session-state synchronisation |
| Molecular / materials / large scientific tasks | Separate CPU/GPU scientific workers |
| AI and voice | Server-side adapters |
| Quantum job | Separate asynchronous adapter |
| Mission history / evidence | Backend, object storage, WorkflowMCP |
| Offline exhibition | Local cached scene and pre-approved result pack |

Recommended modes: browser cloud session for broad access; native PC client for capable devices; warm GPU capacity for exhibitions; local PC-VR as the first VR baseline. Cloud-VR remains experimental until latency and comfort are measured.

Cloud gaming moves cost to GPU-hours, networking, encoding, session management, and support. It does not make compute free.

## 4. Scientific MCP, AI and quantum

The Arctic concept lists 20 logical services: 19 domain endpoints plus one workflow core.

| Family | Count | Domains |
|---|---:|---|
| BioMCP | 6 | Protein/Ligand, RNA/Protein, Protein Design, Protein/Pathway, Enzyme/Protein, Protein/Microbe |
| MaterialsMCP | 5 | Crystal/Molecular, Crystal Lattice, Catalyst/MOF, MOF/Adsorption, Crystal/Ligand |
| TopoMCP | 5 | Node/Crystal, Topology Graph, 3D Topology, Optical/Topology, Quantum Topology |
| EngMCP | 3 | CAD/Material, CAD/Crystal, CAD/Physics |
| WorkflowMCP | 1 | Mission Contract, hashes, reproducible run, evidence and independent validation |

This is a logical service catalogue, not proof all endpoints are deployed in production. Every endpoint needs a status, owner, version, schema, tests, resource profile, licence record, and validator.

Yandex AI Studio / Alice / SpeechKit may be connected through server-side adapters for dialogue, voice, explanations, and structured mission requests, subject to access and commercial terms. Quantum execution is optional: record hardware-versus-emulator status, provider, formulation, job ID, cost, metadata, result hash and classical baseline. Never claim quantum advantage without a task-specific benchmark. Keep API credentials out of the game client.

## 5. Scientific visualisation and procedural animation

Scientific animation should explain data, not merely decorate the scene.

### Protein folding workflow

1. A mission supplies an authorised sequence, structure, or other input.
2. A scientific tool calculates structures, candidate states, or a trajectory.
3. WorkflowMCP records input hashes, tool/model versions, parameters, and outputs.
4. A molecular visualiser displays atoms/residues, backbone, chains, bonds, domains, surfaces, and contacts.
5. Animation interpolates between calculated states or displays available trajectory frames.
6. Players pause, inspect residues, compare candidate states, and view metrics.

**Particle systems do not calculate protein folding.** The scientific backend produces the data; animation and particles visualise it.

### Particle and procedural animation applications

| System | Visual purpose |
|---|---|
| Molecular particles | Atoms, interactions, trajectories, molecular fields |
| Energy landscapes | Candidate states and conceptual transitions |
| Diffusion / transport | Concentration gradients, flows, particle movement |
| Catalysis / reactions | Reaction stages and chemical species |
| Arctic atmosphere | Snow, blowing snow, fog, ice crystals |
| Energy | Heat, gas, hydrogen and flows |
| Sensors | LiDAR point clouds, radar returns, thermal fields |

Use UNIGINE Sequencer, Animation Graph, IK, Look At, joint constraints, procedural pose control, data-driven interpolation, and material parameters in the UNIGINE runtime. Niagara is the Unreal / UEFN VFX system, not the UNIGINE particle system.

### Scientific animation allocation

The existing game WBS already includes **$220,000** for characters, animation, VFX, audio, and music. This is an allocation inside that line, not an extra:

| Sub-package | Allocation |
|---|---:|
| Molecular renderer and structure representation | $45,000 |
| Trajectory / conformational-state interpolation | $35,000 |
| Particles for energy, diffusion, reactions and flows | $25,000 |
| Procedural controllers, timelines and scientific transitions | $15,000 |
| **Scientific animation allocation** | **$120,000** |
| Remaining character/vehicle animation, general VFX, audio and music | $100,000 |
| **Original package total** | **$220,000** |

## 6. Game production budget — base case

This is the working planning WBS, not audited historical spend, a contractor quote, or a signed fixed-price contract.

### 6.1 Core game WBS

| Work package | Base USD |
|---|---:|
| Discovery, requirements and technical qualification | $140,000 |
| Core runtime, mission system, saves and progression | $480,000 |
| Arctic terrain, exterior and seven station zones | $650,000 |
| Rusak K-7 vehicle model and physics | $390,000 |
| Snegir electric snowmobile | $150,000 |
| Roof communications system / drone gameplay | $160,000 |
| Weather, snow, wind, polar day and aurora | $330,000 |
| Vegetation, seasons and wildlife behaviour | $190,000 |
| Missions, campaign, economy and interaction design | $420,000 |
| Characters, animation, VFX, audio and music | $220,000 |
| UI/UX, maps, vehicle HUD and localisation | $150,000 |
| Multiplayer, accounts, sessions and state persistence | $260,000 |
| AI assistant and in-game Scientific MCP integration | $190,000 |
| QuantumCompute adapter and benchmark demo | $90,000 |
| PC-VR / OpenXR | $320,000 |
| VK Play build, SDK, packaging and release requirements | $90,000 |
| Nanosemantics / MIPT stand software integration | $230,000 |
| QA, performance, VR comfort, compatibility and security | $300,000 |
| Production management, documentation, rights and delivery | $240,000 |
| Exhibition hardware allowance | $75,000 |
| Engine, middleware and data licence allowance | $80,000 |
| Initial launch marketing | $250,000 |
| **Core game WBS subtotal** | **$5,405,000** |
| Contingency — 15% | $810,750 |
| **Core game budget** | **$6,215,750** |

The $230,000 stand line is software integration, not the price of the physical Nanosemantics stand. The $75,000 is an equipment allowance, not a confirmed purchase.

### 6.2 Additional Cloud Gaming / WebStream package

| Work package | Base USD |
|---|---:|
| UNIGINE WebStream integration and server runtime profile | $85,000 |
| Session broker, lifecycle and autoscaling | $75,000 |
| Signalling / STUN / TURN / WebRTC gateway and authentication | $60,000 |
| Browser thin client: keyboard, mouse, touch and gamepad | $55,000 |
| Encoding profiles, adaptive quality, bitrate and FPS | $65,000 |
| Cloud deployment, containers, observability and recovery | $55,000 |
| Load, network-quality, soak and compatibility tests | $50,000 |
| Security, cost metering and session quotas | $25,000 |
| **Cloud Gaming WBS subtotal** | **$470,000** |
| Contingency — 15% | $70,500 |
| **Cloud Gaming package** | **$540,500** |

### 6.3 Updated game budget

| Scenario | Core game | Cloud Gaming | Total |
|---|---:|---:|---:|
| Lean | $3,824,800 | $280,000 | **$4,104,800** |
| Base | $6,215,750 | $540,500 | **$6,756,250** |
| High | $10,512,000 | $840,000 | **$11,352,000** |

**Base game production with cloud access: $6,756,250.**

The Bank of Russia USD rate on 14 November 2026 was **$1 = ₽82.1516**; the base game converts to approximately **₽555.0 million** at that dated rate.

### 6.4 Scope boundary

The $6.756m includes game production, world/environment, vehicles, weather, missions, multiplayer, PC-VR profile, client-side AI/MCP and quantum demonstrations, stand software integration, exhibition hardware allowance, and Cloud Gaming/WebStream engineering.

It excludes:
- the separate production Scientific Control Plane / Operational Station Twin / MCP backend ($3.4987m);
- unlimited player streaming or dedicated GPU capacity for any future peak;
- manufacturing real vehicles, radar, communications hardware or UAVs;
- building the physical MAS station;
- purchasing a physical quantum computer;
- unlimited 24/7 premium cloud support.

## 7. Full Scientific Platform — separate CAPEX

| Platform work package | Base USD |
|---|---:|
| Mission Control Plane / tenants / mission registry | $280,000 |
| WorkflowMCP / evidence / independent validation | $350,000 |
| BioMCP — six logical endpoints | $360,000 |
| MaterialsMCP — five logical endpoints | $300,000 |
| TopoMCP — five logical endpoints | $325,000 |
| EngMCP — three logical endpoints | $210,000 |
| Operational Virtual Station data model | $400,000 |
| Yandex AI / Alice / GitVerse adapters | $150,000 |
| Security / tenancy / DevSecOps / observability | $250,000 |
| Operator console / developer portal / SDK | $120,000 |
| Scientific QA / benchmarks / conformance tests | $130,000 |
| Deployment / backup / runbooks / SRE readiness | $90,000 |
| **Platform WBS subtotal** | **$2,965,000** |
| Contingency — 18% | $533,700 |
| **Scientific Platform CAPEX** | **$3,498,700** |

### Combined project

| Component | Base USD |
|---|---:|
| Game with Cloud Gaming | $6,756,250 |
| Full Scientific Platform | $3,498,700 |
| **Combined CAPEX** | **$10,254,950** |
| Game fixed annual OPEX | $860,000 |
| Platform fixed annual OPEX | $1,357,000 |
| **Combined fixed annual OPEX** | **$2,217,000** |
| **CAPEX + first 12 months fixed OPEX** | **$12,471,950** |

Variable cloud gaming is additional and depends on actual stream-hours, GPU density, networking, encoding, region and concurrency.

## 8. Cloud Gaming unit economics — illustrative

Cloud.ru’s published tariff effective 9 September 2026 lists a VM with **2 × NVIDIA A100 80 GB NVLink** at **₽854 per VM-hour including VAT**. At the Bank of Russia rate of ₽82.1516/USD (14 November 2026), this is about **$10.39 per VM-hour**.

| Concurrent sessions on one 2-GPU VM | GPU cost per stream-hour |
|---:|---:|
| 2 sessions (1 per GPU) | ~$5.20 |
| 4 sessions (2 per GPU) | ~$2.60 |
| 8 sessions (4 per GPU) | ~$1.30 |

These densities are **test scenarios, not measured A100 performance**. Actual results depend on scene complexity, resolution, FPS, encoder, CPU, memory, physics and quality target.

A 6 Mbps stream transfers approximately 2.7 GB per hour. **Do not apply an Object Storage egress tariff to game-server streaming as if it were automatically the VM network tariff.** Compute egress/CDN/networking must be quoted separately.

| Delivered stream-hours/month | Conservative GPU-only | Base GPU-only | Optimised GPU-only |
|---:|---:|---:|---:|
| 2,000 | ~$10,400 | ~$5,200 | ~$2,600 |
| 10,000 | ~$52,000 | ~$26,000 | ~$13,000 |
| 50,000 | ~$260,000 | ~$130,000 | ~$65,000 |

Benchmark one representative scene at 720p/1080p and 30/60 FPS with 1/2/4/8 concurrent sessions before reserving capacity or publishing a fixed per-hour price.

## 9. Scientific Cloud / AI / QPU operating allowance

| Cost category | USD/month |
|---|---:|
| CPU / control plane | $2,246 |
| A100 scientific worker pool (burst) | $1,811 |
| H100 scientific worker pool (burst) | $1,323 |
| Hot object storage | $350 |
| Cold object storage | $151 |
| Storage egress allowance | $723 |
| Network / backup / operations reserve | $301 |
| **Cloud infrastructure reference** | **$6,906** |
| AI / voice API cap | $2,000 |
| Experimental QPU reserve | $2,083 |
| **Scientific Cloud + AI + QPU** | **$10,989/month** |
| **Annual reference** | **$131,868/year** |

This is already included in the platform’s $1.357m fixed annual OPEX. It excludes mass player rendering. Do not count it twice. It is a planning profile, not a provider quotation; compare Cloud.ru, VK Cloud, and Nubes using identical specifications.

## 10. Comparison with other game budgets

These projects differ in genre, teams, development periods, marketing, distribution, and scope. The figures are **reported plans or media estimates**, not audited like-for-like cost statements.

| Project | Public reference | Foldnite game ($6.756m) share |
|---|---:|---:|
| Lesta: announced AAA online project | $25–30m | 22.5–27.0% |
| MIR-A: average of 3 planned games | ₽2.4bn ≈ $29.2m at reference FX | ~23.1% |
| Atomic Heart: one media estimate | At least $25m; official budget undisclosed | ~27.0% |

- **Lesta:** $25–30m was reported for a specific announced AAA multiplayer project including marketing. It is not the average budget for all Lesta games or verified actual spend.
- **MIR-A:** ₽7.2bn is a reported planning budget for three projects; ₽3.6bn was described as external funding sought. ₽2.4bn per game is an arithmetic average, not an independently confirmed budget for each title.
- **Atomic Heart:** the developer did not disclose a definitive budget. Media reporting contains differing estimates; “at least $25m” is one reported estimate, not a confirmed figure.

Foldnite is not a smaller clone of these games. It is a scientific interactive product with cloud rendering, scientific integrations, simulation, and a separate enterprise platform. The comparison gives order-of-magnitude context only.

## 11. Delivery plan and acceptance gates

| Stage | Indicative months | Required evidence |
|---|---:|---|
| Discovery and rights review | 0–2 | Scope, permissions, data, asset audit, target platforms |
| Technical pre-production | 2–4 | Engine/licence choice, terrain pipeline, cloud-stream POC |
| Vertical slice | 4–7 | One station zone, mission, vehicle, weather, streaming test |
| Main production | 7–13 | Remaining zones, vehicles, environment, missions and VFX |
| Systems integration | 12–16 | Multiplayer, AI/MCP, session manager, PC-VR, persistence |
| Alpha / Beta | 16–19 | Load, latency, session cost, scientific and gameplay QA |
| Release candidate | 20 | VK Play package, deployment runbook, support and compliance |

Cloud benchmark: representative scene; confirm licence; test 720p/1080p at 30/60 FPS; test 1/2/4/8 sessions; measure glass-to-glass latency, dropped frames, packet loss, CPU/GPU use and bitrate; run an 8-hour soak test; calculate cost per successful stream-hour; only then reserve GPU capacity.

## 12. Status discipline

- **LIVE** — deployed and available to users.
- **TESTED** — reproducible test completed and recorded.
- **PROTOTYPE** — working demonstration, not production service.
- **PLANNED** — design or roadmap item.

Do not claim all 20 MCP services are production-ready without endpoint-level evidence. Do not call an emulator a QPU. Do not claim quantum advantage without a benchmark. Distinguish live station telemetry, imported data, simulation, AI output, and scientific computation.

## 13. Sources

- Foldit: https://fold.it/
- Scientific games / Foldit research overview: https://pmc.ncbi.nlm.nih.gov/articles/PMC8297398/
- UNIGINE SDK 2.22: https://unigine.com/ru/news/2026/unigine-sdk-2-22-release
- UNIGINE documentation: https://developer.unigine.com/
- UEFN: https://dev.epicgames.com/documentation/fortnite/unreal-editor-for-fortnite
- Niagara: https://dev.epicgames.com/documentation/fortnite/niagara
- Epic Pixel Streaming: https://dev.epicgames.com/documentation/unreal-engine/pixel-streaming-in-unreal-engine
- Cloud.ru Evolution GPU tariff: https://cloud.ru/documents/tariffs/evolution/evolution-compute-gpu
- Cloud.ru Evolution Compute: https://cloud.ru/documents/tariffs/evolution/evolution-compute
- Cloud.ru Object Storage: https://cloud.ru/documents/tariffs/evolution/object-storage
- Bank of Russia USD rate, 14 November 2026: https://www.cbr.ru/currency_base/daily/?UniDbQuery.Posted=True&UniDbQuery.To=14.11.2026
- Lesta reporting: https://habr.com/ru/news/777284/
- MIR-A portfolio reporting: https://habr.com/ru/news/1015536/
- MIR-A official site: https://miragamestudio.ru/
- Atomic Heart estimate caveats: https://www.rbc.ru/technology_and_media/11/03/2023/6409d2679a7947212cbc25f7

## 14. Executive financial summary

| Measure | Base estimate |
|---|---:|
| Game production including Cloud Gaming engineering | **$6,756,250** |
| Separate Scientific Platform CAPEX | **$3,498,700** |
| **Combined CAPEX** | **$10,254,950** |
| Combined fixed annual OPEX | **$2,217,000/year** |
| CAPEX + first 12 months fixed OPEX | **$12,471,950** |
| Scientific cloud / AI / QPU | **$131,868/year**, already included in platform OPEX |
| Player cloud rendering | **Variable; measure and bill by delivered stream-hours** |

**Product principle:** players use an accessible client; the cloud carries demanding rendering and scientific workloads; scientific animation visualises calculated data; WorkflowMCP records what was computed and checked.
