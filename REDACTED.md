# 🕵️ Redacted — Noir Detective Murder Mystery App
### *Top Secret Case Files & Procedural Investigation Game*

---

## 📌 1. Executive Summary & Concept

**Redacted** (`com.redacted.detective`) is an immersive, retro noir detective murder mystery simulation game built natively for Android using modern **Jetpack Compose**, **Android Jetpack Room**, and **Generative AI (Gemini 1.5 Flash & OpenAI-compatible LLMs)**.

Set in the gritty atmosphere of the **1980–2010 analog-to-digital transition era** (frequently featuring evocative Kolkata / Bengal backdrops such as the Salt Lake Cyber Hub, Lalbazar Detective Bureau, and analog telecommunications nodes), the game puts players in the shoes of a detective investigating classified homicide dossiers.

The application combines classic **fair-play murder mystery deduction** (in the tradition of Agatha Christie, Arthur Conan Doyle, and Sharadindu Bandyopadhyay's Byomkesh Bakshi) with cutting-edge **Generative AI roleplaying and procedural narrative generation**, wrapped in a distinctive **tactile manila case folder** aesthetic.

---

## 🎮 2. What the App Does (Core Gameplay & Mechanics)

```
+-----------------------------------------------------------------------------------+
|                              DETECTIVE GAMEPLAY LOOP                              |
|                                                                                   |
|  [ Detective Login ] -> [ Case Picker / AI Generation ] -> [ Classified Dossier ] |
|                                                                       |           |
|                                                                       v           |
|   +-------------------------- INVESTIGATION (20 AP) ---------------------------+  |
|   |  - Interrogate Suspects (Live AI Roleplay / Offline Emotion Engine)        |  |
|   |  - Crime Scene Search (Examine Body & Search Crime Room)                   |  |
|   |  - Forensic Analysis (5s Simulated Chemical/Ballistic/Digital Turnaround)  |  |
|   +----------------------------------------------------------------------------+  |
|                                       |                                           |
|                                       v                                           |
|  [ Formal Accusation ] -> [ Culprit & Motive Evaluation ] -> [ Truth & Solution ] |
|                                       |                                           |
|                                       v                                           |
|               [ XP Reward & Detective Rank Advancement (+100 XP) ]                |
+-----------------------------------------------------------------------------------+
```

### Key Gameplay Systems:
1. **Detective Call-Sign & Profile Management**:
   - Players register unique detective profiles with persistent stats: **XP**, **Detective Rank**, **Cases Solved**, and **Total Games Played**.
   - Progressive ranks scale from **Rookie (`শিক্ষানবিশ`)** $ightarrow$ **Constable** $ightarrow$ **Detective** $ightarrow$ **Inspector** $ightarrow$ **Chief** $ightarrow$ **Legend (`কিংবদন্তি`)**.

2. **6-Genre Era Matrix Case Selection**:
   - Players can filter or generate procedural cases across six distinctive 1980–2010 mystery genres:
     - 🕵️ **Cold War Espionage**: KGB/CIA sleeper nodes, defector mysteries, coded diplomatic dispatches.
     - 💾 **Early Internet & BBS**: Dial-up networks, modem rooms, midnight bandwidth theft, floppy disk sabotage.
     - 🏢 **Corporate Raiders**: Hostile takeovers, ledger audits, insider embezzlement, white-collar sabotage.
     - 📼 **Analog to Digital**: Magnetic tapes, VHS footage, pagers, CRT monitors, wiretaps.
     - 🎵 **Music Industry Bootlegging**: Record label corruption, cassette pirating syndicates, studio murders.
     - 🔬 **Academic & Lab Espionage**: Stolen research formulas, laboratory rivalries, tenure warfare.

3. **Classified Case Dossier & Narrative Briefing**:
   - Each case begins with a comprehensive **200+ word narrative backstory**, classified evidence photo ID stamp, victim identification, specific cause of death, timestamp, and incident location.

4. **Action Point (AP) Resource Management**:
   - Detectives start with a budget of **20 Action Points (AP)** per case.
   - Every interrogation question, scene search, or forensic lab test consumes 1 AP, requiring players to deduce efficiently before the culprit flees or time runs out.

5. **Crime Scene Searches & Forensic Laboratory**:
   - **Search Body (`🔍 Body`)**: Uncovers physical trauma, victim belongings, and autopsy notes.
   - **Search Room (`🚪 Room`)**: Uncovers hidden objects, sabotaged mechanisms, and footprint/tool evidence.
   - **Forensic Lab (`🧪 Lab`)**: Dispatches evidence for simulated asynchronous laboratory processing (5-second chemical/ballistics breakdown) that reveals the conclusive technical clue (`labClue`).

6. **Suspect Interrogations**:
   - Direct, freeform conversational questioning with each suspect.
   - Suspects react dynamically based on their background, secrets, alibis, relationship to the victim, and whether or not they committed the crime.

7. **Accusation, Keyword Matching & Case Closure**:
   - Detectives select the prime suspect and write down the culprit's motive.
   - An intelligent keyword evaluation algorithm cross-references the written explanation against the required mystery keywords.
   - Upon accusation, the game presents the **full solution breakdown**, displays the true sequence of events, and awards XP (+100 XP for success, +10 XP for cold cases).

---

## 🧠 3. Special Highlight: The AI Architecture & Features

The Generative AI engine serves as the **creative brain and live dungeon master** of REDACTED. The app supports both **Google Generative AI (Gemini 1.5 Flash)** and any **OpenAI-compatible API endpoint (such as DeepSeek Chat, OpenAI, or Local LLMs)**.

### A. Procedural Case Generation (Strict JSON Schema)
Rather than simple text snippets, the AI generates complex, mathematically sound, interconnected mystery webs containing:
- **Rich Narrative**: Multi-layered backstory setting the scene in 1980–2010 settings without anachronisms (no smartphones or modern cloud tech; strictly payphones, pagers, floppy disks, cassette tapes, fax machines).
- **Suspect Roster**: Distinct suspects, each with a unique persona, verified/unverified alibi, true psychological motive, secret (non-murder hidden shame), and behavioral quirks.
- **5-Stage Evidence Tree**:
  1. `initial`: 2 immediate surface clues at the scene.
  2. `bodySearch`: 2 clues discovered upon physical autopsy examination.
  3. `roomSearch`: 2 environmental clues uncovered through meticulous searching.
  4. `labClue`: Technical/forensic/chemical analysis output.
  5. `smokingGun`: The decisive piece of evidence linking the true killer.
- **Evaluation Criteria**: `motiveKeywords` and `solution` providing fair-play verification.

### B. Dynamic Suspect Roleplay & Emotion Engine
During live interrogations, the AI adopts the persona of the questioned suspect with strict roleplaying guardrails:
- **Guilty Suspect Behavior**:
  - Never admits guilt unless confronted with conclusive proof.
  - Deflects suspicion onto other characters and crafts subtle timeline inconsistencies.
  - Shows escalating nervousness when evidence matching their crime is brought up.
- **Innocent Suspect Behavior**:
  - Genuinely cooperative but guarded.
  - If hiding an unrelated secret (embezzlement, bootlegging, infidelity), displays nervous tension regarding *that* secret rather than the homicide.
  - Confident in their true alibi and offers circumstantial observations about other suspects.

### C. Bilingual Generative Prompting (English & Bengali / বাংলা)
The AI system prompts feature complete dual-language prompting matrices:
- Prompts enforce authentic Bengali cultural idioms, vocabulary, and period-appropriate Kolkata landmarks (IISER, Salt Lake Cyber City, vintage observatories).
- Ensures seamless character immersion in both English and Bengali scripts.

### D. Intelligent Offline Fallback & Emulation Engine
If an internet connection is unavailable or no API key is provided, the app falls back to a deterministic **Offline Case & Dialogue System** (`OfflineCases.kt`):
- Pre-packaged multi-layered cases in both languages.
- **Suspicion Meter (0–100%)**: Dynamically calculated based on discovered evidence linked to each suspect.
- **Repetitive Question Detection**: Detects redundant questions and responds with authentic annoyed responses.
- **Emotional Prefix & Punctuation Shifting**: Alters tone, pauses (`...`), and exclamation marks based on the suspect's current stress level.

---

## 🏗️ 4. How It Is Made (Architecture & Tech Stack)

```
+---------------------------------------------------------------------------+
|                           ANDROID ARCHITECTURE                            |
|                                                                           |
|   +-------------------------------------------------------------------+   |
|   |              PRESENTATION LAYER (Jetpack Compose M3)              |   |
|   |  - AppContent & Navigation State Machine                          |   |
|   |  - Responsive Layouts (Mobile Tabbed / Tablet Split-Pane)         |   |
|   |  - Tactile Dossier & Custom Manila Folder Design System           |   |
|   +-------------------------------------------------------------------+   |
|                                     |                                     |
|                                     v                                     |
|   +-------------------------------------------------------------------+   |
|   |                 VIEWMODEL LAYER (AndroidViewModel)                |   |
|   |  - GameViewModel & GameUiState (Immutable StateFlow)              |   |
|   |  - Coroutine Dispatchers (IO / Default)                           |   |
|   |  - AI Prompt Engine & JSON Stream Cleaners                        |   |
|   +-------------------------------------------------------------------+   |
|                                     |                                     |
|                  +------------------+------------------+                  |
|                  v                                     v                  |
|   +-----------------------------+       +-----------------------------+   |
|   |    DATA LAYER (Room DB)     |       |    AUDIO ENGINE (PCM)       |   |
|   |  - RedactedDatabase (v3)    |       |  - SoundManager             |   |
|   |  - Cascade Foreign Keys     |       |  - Low-level AudioTrack     |   |
|   |  - Users/Cases/Suspects/    |       |  - Real-time Sine Wave      |   |
|   |    Evidence/Notes DAOs      |       |    Frequency Synthesis      |   |
|   +-----------------------------+       +-----------------------------+   |
+---------------------------------------------------------------------------+
```

### Technical Specifications:
- **Language**: 100% Kotlin (Version `1.9.22`) with Gradle Kotlin DSL (`build.gradle.kts`, `settings.gradle.kts`).
- **Android Target**: Android 14 (API 34), Minimum SDK 26 (Android 8.0 Oreo).
- **UI Toolkit**: Modern declarative **Jetpack Compose** with **Material 3**, custom monospace styling, retro folder tilt animations (`rotate(-0.3f)`), and dual adaptive layouts (tablet split-pane vs mobile tabbed navigation).
- **Local Persistence**: **Room Database 2.8.4** backed by **KSP (Kotlin Symbol Processing)**:
  - `UserEntity`: Profile tracking, XP, rank index, login timestamps.
  - `CaseEntity`: Complete case metadata, narrative backstory, solution keys, bookmark/saved status.
  - `SuspectEntity`: Linked via `ForeignKey.CASCADE` on `caseId`.
  - `EvidenceEntity`: Structured evidence items with discovery flags.
  - `NoteEntity`: Chronological investigation notebook and interrogation logs.
- **Audio Engine (`SoundManager.kt`)**:
  - Completely custom **software synthesizer** using Android's low-level `AudioTrack` and PCM 16-bit encoding.
  - Mathematically generates sine wave frequencies on the fly for typewriter clicks (800 Hz), discovery chimes (1200 Hz -> 1800 Hz), success triads (440 Hz -> 554 Hz -> 659 Hz), and failure buzzers (150 Hz -> 100 Hz). Zero external `.mp3` or `.wav` asset overhead.
- **Multi-Provider AI Networking**:
  - Google Gemini Generative AI SDK (`com.google.ai.client.generativeai:generativeai:0.9.0`).
  - Native lightweight HTTP JSON client for OpenAI/DeepSeek-compatible `/chat/completions` endpoints.
  - Configurable `local.properties` build-time credentials injection via `BuildConfig`.

---

## ✨ 5. What Makes REDACTED Unique & Interesting

1. **Unique Tactile Aesthetic & Atmosphere**:
   - The UI avoids cookie-cutter modern flat design in favor of a tactile **vintage confidential dossier on a dark mahogany desk** (`BgWood = 0xFF2C241B`, `FolderColor = 0xFFF0E6D2`, `PaperColor = 0xFFFDFBF7`, `InkColor = 0xFF2B2B2B`, `StampRed = 0xFFD32F2F`).
   - Monospace typography, classified photo frames, typewriter-inspired audio, and red stamp badges evoke classic detective cinema.

2. **Fair-Play Detective Mechanics**:
   - Unlike random guessing games or trivia apps, REDACTED adheres strictly to the Golden Age principles of detective fiction: all necessary clues to solve the crime are discoverable through thorough interrogation and scene investigation.

3. **Period-Accurate Nostalgia (1980–2010)**:
   - Setting stories in the dawn of the internet, BBS networks, cassette piracy, and early mobile communications provides a rich, atmospheric playground free of ubiquitous smartphones or modern cloud computing shortcuts.

4. **Authentic Regional Culture & Deep Bilingual Immersion**:
   - Rich homage to Bengali detective traditions (Feluda, Byomkesh Bakshi, Kakababu), featuring genuine cultural references, authentic dialect variations, and atmospheric settings across Bengal and Kolkata.

5. **Zero-Asset Procedural Audio**:
   - The entire soundscape is synthesized in real-time math, keeping APK size lightweight while offering snappy, instant acoustic feedback.

6. **Privacy-Preserving & Local-First Architecture**:
   - All detective progress, cases, notebook entries, and bookmarks are stored strictly on-device in a local Room database, requiring no external user tracking or mandatory cloud logins.

---

## 📊 6. Summary Matrix

| Metric / Dimension | Implementation Detail |
| :--- | :--- |
| **App Title** | REDACTED (Detective Case Files) |
| **Package** | `com.redacted.detective` |
| **Primary Platform** | Android (Kotlin, Jetpack Compose, Material 3) |
| **AI Models Supported** | Gemini 1.5 Flash, DeepSeek Chat, OpenAI-compatible models |
| **Database** | Jetpack Room SQLite Database with cascading relational entities |
| **Audio** | Real-time PCM Sine Wave Synthesis (`AudioTrack`) |
| **Game Modes** | Online Generative AI Mode + Fully Offline Pre-Authored Mode |
| **Languages** | English & Bengali (বাংলা) |
| **Core Themes** | Retro Noir, 1980–2010 Analog Mystery, Kolkata/Bengal settings |

---
*Report generated for REDACTED Project Overview & Technical Architecture.*
