# Foldnite Arctic — MAS “Snezhinka”

**A scientific game world based on the Arctic research station MAS “Snezhinka”.**

![](https://foldnite.github.io/arctic/assets/img/mas-sn2.jpg)

Foldnite combines **STEM + Foldit-inspired scientific problem-solving + Fortnite-inspired worlds (UEFN) + quantum computing**. Players explore the station, operate virtual equipment, travel across the Arctic, and solve team missions.

> This is a planning document, not a vendor quotation, approved funding commitment, or proof that every proposed feature is already implemented.

## 1. Product scope

The world is planned around seven station domains: energy; climate and environment;
1. biology and medicine;
2. robotics and transport; 
3. materials and engineering; 
4. connectivity and control; 
5. living and life support.

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
