# 💖 PyaarAI — Comprehensive Project & Architecture Report

> **A deeply empathetic romantic companion, Urdu/Hindi poet, and tactile scrapbook assistant engineered for modern Indian relationships.**

---

## 1. Executive Summary

**PyaarAI** is a modern, native Android application engineered to celebrate and nurture romantic relationships through the power of generative AI, culturally attuned poetry, tactile scrapbook journaling, and physical merchandise design. 

Unlike generic AI conversational tools, PyaarAI is designed from the ground up to understand the emotional and cultural nuances of Indian couples — balancing the poetic grandeur of classical Urdu/Hindi *Shayari* (in Devanagari and Hinglish) with contemporary relationship counseling frameworks, memory preservation, and tangible gift personalization.

`
       ┌─────────────────────────────────────────────────────────────┐
       │                       PyaarAI App                           │
       ├──────────────┬──────────────┬───────────────┬───────────────┤
       │   AI Poetry  │  Gift Mockup │   Scrapbook   │   WhatsApp    │
       │    Studio    │    Studio    │   Timeline    │   Card Share  │
       └───────┬──────┴──────┬───────┴───────┬───────┴───────┬───────┘
               ▼             ▼               ▼               ▼
       ┌──────────────┬──────────────┬───────────────┬───────────────┐
       │   DeepSeek   │ Custom 2D/3D │  3D Polaroid  │ Compose Layer │
       │  AI Engine   │ Canvas Render│ Room Database │ Rasterization │
       └──────────────┴──────────────┴───────────────┴───────────────┘
`

---

## 2. What the App Does (Functional Scope & Feature Set)

PyaarAI provides a holistic relationship ecosystem combining emotional expression, relationship memory archiving, and customized gift design.

### 2.1. Couple Dossier & Relationship Onboarding
* **Intimate Profile Setup:** Captures both partners' names, personal pet names/nicknames, anniversary date, inside jokes, language preference (*Hinglish, Hindi, Urdu, English*), and primary love languages (*Words of Affirmation, Quality Time, Acts of Service, Physical Touch, Receiving Gifts*).
* **Relationship Pulse Dashboard:** Real-time relationship milestone counter (anniversary countdowns / days together) and daily contextual prompts.

### 2.2. The AI Expression & Poetry Studio
Generates tailored, high-emotion romantic content across six distinct categories:
1. **Shayari (शायरी):** Classical 4-line (2-Sher) poetic couplets adhering to traditional meter (*Qaafiya* and *Radeef*) with timeless romantic themes.
2. **Love Letters:** Multi-paragraph, handwritten-style letters that organically weave shared memories into heartfelt emotional prose.
3. **Micro-Poems:** Modern, minimalist, 3–5 line rhyming verses optimized for phone wallpapers and romantic lock-screens.
4. **Apologies & Reassurance:** Emotionally intelligent conflict-resolution messages built on psychological repair principles.
5. **Morning Status Messages:** Conversational, emoji-rich, affectionate check-ins designed for quick messaging.
6. **Gift Inscriptions:** Symmetrical 2-line rhyming couplets (10–18 words) optimized for physical gift printing.

### 2.3. Physical Gift Mockup Studio (Custom Merch Studio)
* **Real-Time Product Visualizer:** Dynamically renders custom romantic couplets and generated poetry onto three physical product types:
  * **Ceramic Coffee Mugs:** With curved cylindrical surface simulation, lighting highlights, and realistic ceramic handles.
  * **Heavyweight Graphic T-Shirts:** With crewneck collar lines, fabric shading, and chest imprint placement.
  * **Acrylic Glass Keepsake Frames:** With clear glass borders, beveled drop shadows, and minimalist wooden easel stands.
* **Studio Controls:** Color palette switcher (*Ivory, Sky Blue, Rose Pink, Lilac, Sage Green, Kraft*), dynamic font scale slider, typography selector (*Dancing Script, Caveat, Serif, Clean Sans*), and live text alignment.
* **Instant HD Snapshot Export:** One-tap export that captures the mockup as a high-resolution PNG for direct sharing or printing.

### 2.4. Tactile Scrapbook Timeline (Memory Lane)
* **3D Interactive Polaroid Cards:** Memory cards rendered with realistic paper borders and washi tape accents that flip in 3D on tap to reveal hidden romantic notes and scribbles.
* **Media Attachment:** Allows users to attach local camera and gallery photos to create an immutable chronological relationship reel.
* **Emotional Mood Tagging:** Categorizes moments by mood (*Joyful, Cozy, Romantic, Nostalgic*).

### 2.5. Saved Notes & Heart Library
* **Personalized Archive:** Bookmarks favorite generations with filter toggles for category, mood, and favorites.
* **5-Star Like Feedback Loop:** Users can Heart creations, automatically training the in-app AI prompt generator to mirror the rhythm, vocabulary, and intimacy of beloved creations in future sessions.
* **Direct WhatsApp Card Sharing:** Generates custom-rendered parchment cards with torn edges and doodle decorations that can be shared directly to WhatsApp with a single click.

---

## 3. How PyaarAI is Made (Technical Architecture & Engineering)

PyaarAI is built strictly adhering to modern Android engineering best practices, Clean Architecture, and Unidirectional Data Flow (UDF).

`
┌────────────────────────────────────────────────────────────────────────┐
│                          PRESENTATION LAYER                            │
│  Jetpack Compose • Material 3 • Custom Canvas • Navigation Component  │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │ (Observes UI State / Sends Intents)
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│                            VIEWMODEL LAYER                             │
│       Kotlin Coroutines • StateFlow • SharedFlow • UDF State Machine   │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │ (Calls Domain & Data Repositories)
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│                               DATA LAYER                               │
│  ┌───────────────────────────┐          ┌───────────────────────────┐  │
│  │     Local Persistence     │          │    Remote & AI Engine     │  │
│  │ • Room Database (v4)      │          │ • OkHttp 3 ConnectionPool │  │
│  │ • DataStore Preferences   │          │ • DeepSeek Chat API       │  │
│  │ • FileProvider Cache      │          │ • Streaming SSE Flow      │  │
│  └───────────────────────────┘          └───────────────────────────┘  │
└────────────────────────────────────────────────────────────────────────┘
`

### 3.1. Core Tech Stack Matrix

| Layer | Technologies / Libraries | Purpose |
| :--- | :--- | :--- |
| **Language** | Kotlin 1.9+ | 100% Kotlin codebase leveraging modern language idioms and Coroutines. |
| **UI Framework** | Jetpack Compose + Material 3 | Declarative, reactive UI with custom canvas drawing and hardware-accelerated layouts. |
| **Architecture** | MVVM + Clean Architecture | Unidirectional Data Flow (UDF) with robust separation of concerns. |
| **Local Database** | Room Persistence Library v4 | SQLite object mapping with composite indexing for high-speed offline access. |
| **Preferences** | Jetpack DataStore (Preferences) | Reactive, non-blocking asynchronous key-value storage for settings and theme state. |
| **Networking** | OkHttp 3 & Gson | Persistent HTTP/2 connection pooling with streaming Server-Sent Events (SSE) support. |
| **AI LLM Engine** | DeepSeek Chat API (deepseek-chat) | High-reasoning language model configured with dynamic temperature and custom system personas. |
| **Graphics & Export** | Compose GraphicsLayer + Android Canvas | In-memory bitmap rasterization and software-safe hardware bitmap extraction. |
| **Image Loading** | Coil Compose | Asynchronous image loading and disk caching for scrapbook polaroid memories. |
| **OS Integration** | Android FileProvider & Intent System | Secure, sandboxed file sharing with automatic cache pruning for WhatsApp sharing. |

### 3.2. Custom Canvas & Visual Rendering Pipeline
* **Procedural Torn Paper (TornPaperBox.kt):** Uses custom GenericShape and Path algorithms that generate realistic, jagged torn-paper silhouettes with configurable tear depths, step widths, and paper grain noise.
* **Zero-Allocation Static Specks:** Static speckle patterns are pre-computed and cached to maintain steady 120 FPS rendering during complex list scrolling without triggering Garbage Collection (GC) pauses.
* **Dynamic Doodle Markers:** Custom parser (parseDoodleMarkers) translates embedded AI tags (e.g. <heart>, <star>, <flower>, <sparkle>, <underline>) into interactive hand-drawn vector doodle overlays positioned seamlessly around text.

---

## 4. Special Highlight: The AI Architecture & Features

The intelligence layer of PyaarAI is not a simple wrapper around an API; it is a multi-tier prompt engineering and context-injection system built specifically for emotional accuracy, cultural grounding, and zero repetition.

`
                  ┌─────────────────────────────────────────┐
                  │          Generation Request             │
                  │   Category, Mood, Dossier, Language     │
                  └────────────────────┬────────────────────┘
                                       │
      ┌────────────────────────────────┼────────────────────────────────┐
      ▼                                ▼                                ▼
┌──────────────┐             ┌──────────────────┐             ┌──────────────────┐
│  Anti-Dup    │             │   Liked Style    │             │  Couple Dossier  │
│ Fingerprints │             │    Exemplars     │             │ Context Injection│
│ (Avoid List) │             │ (Few-Shot Prompt)│             │ (Names/Anniv/JL) │
└──────┬───────┘             └────────┬─────────┘             └────────┬─────────┘
       │                              │                                │
       └───────────────────────┬──────┴────────────────────────────────┘
                               ▼
            ┌──────────────────────────────────────┐
            │   Dynamic Persona System Prompt      │
            │  (Shayar / Letter / Repair / Engrave)│
            └──────────────────┬───────────────────┘
                               ▼
            ┌──────────────────────────────────────┐
            │      DeepSeek Chat Engine API        │
            │   (Streamed SSE with Dynamic Temp)   │
            └──────────────────┬───────────────────┘
                               ▼
            ┌──────────────────────────────────────┐
            │   Output Doodle Parser & Formatter   │
            │    (Regex Tokenization & Markers)    │
            └──────────────────────────────────────┘
`

### 4.1. Dynamic Category Personas
The system dynamically reconfigures its core prompt persona and system temperature based on the selected generation mode:

1. **The Classical Shayar (SHAYARI | Temp: 0.90):**
   * Operates in the literary traditions of *Mir Taqi Mir, Faiz Ahmed Faiz,* and *Gulzar*.
   * Enforces strict metric discipline: exactly 4 lines (2 complete *Sher*), mandatory *Qaafiya* (rhyme scheme AABB or ABAB), and *Radeef* (refrain).
   * Guardrail: Strict prohibition of English; output must be authentic Devanagari Hindi, Hinglish, or Urdu. Restricts mundane trivia to keep poetry elevated and timeless.

2. **The Gift Inscription Engraver (GIFT_ENGRAVING | Temp: 0.80):**
   * Engineered specifically for physical product geometries (ceramic mugs, t-shirt prints, acrylic frames).
   * Strict physical constraints: Exactly 2 lines (1 Sher), 10 to 18 words total, and symmetrical word counts per line (5–8 words each) so text stays centered on curved surfaces.

3. **The Intimate Correspondent (LONG_LETTER | Temp: 0.75):**
   * Writes in an authentic, imperfect, deeply personal human voice.
   * Restricts output to exactly 2 structured paragraphs, weaving a single shared memory into the emotional arc naturally rather than listing facts robotically.

4. **The Modern Micro-Poet (MICRO_POEM | Temp: 0.85):**
   * Produces 3–5 line aesthetic verses combining sharp contemporary imagery with mandatory end/internal rhymes.

5. **The 5-R Conflict Resolution Counselor (APOLOGY | Temp: 0.65):**
   * Implements the **5-R Psychological Repair Framework**:
     1. *Recognize:* Acknowledge the specific hurt caused.
     2. *Responsibility:* Own the mistake unconditionally (strict rule: never use but after sorry).
     3. *Remorse:* Express genuine empathy.
     4. *Repair:* Offer concrete corrective action.
     5. *Recommit:* Promise tangible growth for the future.

### 4.2. Anti-Duplication & Freshness Fingerprinting
To prevent the common LLM pitfall of repeating standard tropes or identical opening lines across generations:
* Every generation's opening line, closing line, category, language, and mood are hashed and stored in Room (GenerationFingerprintEntity).
* Subsequent prompts query the database for the last 8 generated fingerprints and inject explicit 🚫 ANTI-DUPLICATION MANDATES into the prompt payload, forcing the model to explore completely novel metaphors and imagery.

### 4.3. Exemplar-Guided Tone Learning (Few-Shot Tuning)
* When a user taps the Heart / Like button on a generated creation, it is flagged in the database with a high preference weight.
* Future generation requests query the top 3 highest-rated exemplars and inject them as few-shot reference anchors, instructing the model to match the couple's preferred intimacy cadence, humor, and vocabulary without copying the text verbatim.

---

## 5. What Makes PyaarAI Interesting & Unique

### 5.1. Authentic South Asian Cultural Grounding
Most modern relationship apps are built for Western paradigms and default to generic English. PyaarAI is deeply grounded in the linguistic and cultural realities of South Asia:
* Seamless handling of **Hinglish**, **Devanagari Hindi**, and **Urdu**.
* Poetic depth rooted in authentic South Asian poetic devices rather than generic translated rhymes.

### 5.2. Handcrafted Scrapbook Aesthetic
The UI rejects sterile, flat corporate interfaces in favor of a tactile, romantic scrapbook feel:
* Warm, comforting palette: *Parchment Cream (#FDFBF7), Warm Kraft (#EADCC9), Dark Sepia Ink (#2C221E), and Terracotta Red (#C85A53)*.
* Realistic paper drop shadows, jagged torn-paper dividers, washi tape strips, and animated crayon doodles.
* 3D card flips that simulate inspecting a physical polaroid photo.

### 5.3. The Digital-to-Physical Bridge
PyaarAI does not leave romantic words trapped inside a phone screen. With the **Gift Mockup Studio**, couples can immediately visualize their custom couplets engraved on physical lifestyle products (mugs, t-shirts, frames), turning intangible digital poetry into tangible real-world keepsakes.

### 5.4. Frictionless Social Export
* In-memory visual rendering using Jetpack Compose GraphicsLayer rasterizes the styled parchment card into an image without requiring off-screen Activities.
* Direct integration with WhatsAppShareHelper allows sending beautifully styled picture cards straight into WhatsApp chats in one tap.

### 5.5. Ultra-Optimized Local Performance
* **Composite Database Indices:** Instant retrieval across thousands of saved creations and memories.
* **Self-Pruning FileProvider Cache:** WhatsApp share temporary cache automatically retains only the 3 most recent images, ensuring the app consumes minimal disk storage.
* **Persistent Connection Pooling:** Reuses TCP/TLS connections to the AI server to deliver rapid response times.

---

## 6. Project Directory Structure

`
pyaarai/
├── app/
│   ├── src/main/
│   │   ├── kotlin/com/pyaarai/app/
│   │   │   ├── MainActivity.kt               # Main entry point & theme container
│   │   │   ├── PyaarAIApp.kt                 # Scaffold & Navigation Host
│   │   │   ├── data/
│   │   │   │   ├── ai/
│   │   │   │   │   └── DeepSeekLoveService.kt # AI LLM Engine & Prompt Pipeline
│   │   │   │   ├── local/
│   │   │   │   │   ├── HeartSyncDatabase.kt   # Room Database Definition (v4)
│   │   │   │   │   ├── Dao.kt                 # Reactive Room DAOs (Flows)
│   │   │   │   │   └── Entities.kt            # Dossier, Memory, Fingerprint Entities
│   │   │   │   └── repository/
│   │   │   │       ├── HeartSyncRepository.kt # Central Data Repository
│   │   │   │       └── UserPreferences.kt     # DataStore Preferences Manager
│   │   │   ├── ui/
│   │   │   │   ├── components/                # Reusable UI Components
│   │   │   │   │   ├── TornPaperBox.kt        # Procedural Torn Paper Canvas
│   │   │   │   │   ├── DoodleOverlay.kt       # Hand-drawn Doodles & Tags
│   │   │   │   │   ├── WashiTape.kt           # Scrapbook Tape Accents
│   │   │   │   │   └── PolaroidCard.kt        # 3D Flipping Photo Cards
│   │   │   │   ├── home/                      # Dashboard & Milestone Tracker
│   │   │   │   ├── studio/                    # AI Poetry & Shayari Studio
│   │   │   │   ├── merch/                     # Gift Mockup Studio (Mug/Shirt/Frame)
│   │   │   │   ├── timeline/                  # Scrapbook Timeline (Memory Lane)
│   │   │   │   ├── notes/                     # Saved Creations & Bookmarks
│   │   │   │   ├── onboarding/                # Couple Profile Setup
│   │   │   │   └── settings/                  # AI Config & Theme Settings
│   │   │   ├── theme/                         # Color Palette & Typography
│   │   │   └── util/
│   │   │       └── WhatsAppShareHelper.kt     # Image Rasterization & Share Provider
│   │   └── AndroidManifest.xml
│   └── build.gradle.kts
`

---

## 7. Conclusion

**PyaarAI** represents an innovative fusion of cutting-edge generative AI, culturally resonant natural language prompt engineering, and tactile, emotionally warm mobile interface design. By transforming AI from a generic utility into a thoughtful, creative romantic companion, PyaarAI helps couples celebrate, preserve, and deepen their emotional connection in the digital era.
