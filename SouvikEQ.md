# SouvikEQ – Intelligent Acoustic Studio & System-Wide Audio Equalizer
**Comprehensive Project Report: Core Capabilities, Architecture, and AI Acoustic Intelligence**

---

## 1. Executive Summary

**SouvikEQ** is an advanced, broadcast-grade audio mastering and system-wide equalization application engineered natively for the Android platform. Built entirely in modern Kotlin and Jetpack Compose (Material You), SouvikEQ bridges the gap between complex professional acoustic engineering tools and everyday consumer mobile listening.

Standard Android equalizer applications historically suffer from a fundamental flaw: **they are designed around technical guesswork**. Everyday music listeners know when their music lacks punch, when vocals sound muffled, or when treble causes ear fatigue, but conventional 5-band or 10-band graphic equalizers force them to guess arbitrary decibel numbers across unfamiliar frequencies (e.g., *+4 dB at 230 Hz*, *-2 dB at 3.6 kHz*).

SouvikEQ completely reimagines this experience by combining:
- **A Hardware Mixing Desk Aesthetic**: Tactile studio faders, continuous Bézier parametric curve visualization, and a 32-band reactive spectrum visualizer.
- **System-Wide DSP Audio Interception**: Intercepts and masters audio across any media player on the device (Spotify, YouTube Music, Apple Music, Tidal, local players).
- **The AI Sound Engineer (The Standout Feature)**: A conversational acoustic intelligence companion that interviews the listener about their audio gear and sonic preferences, automatically translating natural language requests into calibrated, mathematically precise DSP filter curves.

---

## 2. What the App Does (Core Capabilities)

### 2.1 System-Wide Audio Processing
SouvikEQ is not restricted to an internal media player. By registering an `AudioSessionReceiver` that listens to Android's `AudioEffect.ACTION_OPEN_AUDIO_EFFECT_CONTROL_SESSION` and `ACTION_CLOSE_AUDIO_EFFECT_CONTROL_SESSION` system broadcasts, SouvikEQ binds directly to global Android audio session IDs (Session 0) and specific media player playback sessions. When active, any audio rendered through Spotify, YouTube, SoundCloud, Netflix, or games is immediately routed through SouvikEQ's DSP pipeline.

### 2.2 5-Band Studio Parametric Equalizer
The core equalization engine provides precise decibel boost and cut capabilities across 5 carefully selected audio frequency bands:
- **60 Hz (Sub-Bass)**: Controls fundamental sub-bass frequencies, sub-kick resonance, and physical rumble.
- **230 Hz (Bass / Warmth)**: Governs basslines, low-register brass, and vocal body warmth.
- **910 Hz (Midrange / Vocal Body)**: Directly shapes acoustic presence, guitar tone, and dialogue intelligibility.
- **3.6 kHz (Upper Midrange / Presence)**: Controls transient attack, snare crack, and perceived vocal proximity.
- **14 kHz (High Treble / Air)**: Adds shimmering air, cymbal brilliance, and psychoacoustic openness.

Gains range from **-12.0 dB to +12.0 dB** with micro-precision dragging, fine-grained decibel readouts, and double-tap zeroing.

### 2.3 Continuous Parametric Frequency Transfer Curve
Unlike basic EQ apps that only show discrete slider points, SouvikEQ computes a real-time **Cubic Bézier parametric curve** across the entire 20 Hz – 20 kHz human hearing spectrum. As the user drags any fader, the curve dynamically plots the continuous acoustic transfer function, complete with gradient fills and decibel grid guides.

### 2.4 32-Band Dynamic Audio Spectrum Visualizer
The top header houses a 32-band neon spectrum analyzer displaying live acoustic harmonics across low, mid, and high frequencies. It features dynamic gradient rendering and automatically enters a standby state whenever the equalizer is toggled off.

### 2.5 3D Spatial Soundstage & Sub-Bass Exciter
Accessible via the dedicated **3D FX** sheet:
- **3D Spatializer (Virtualizer)**: Employs Head-Related Transfer Function (HRTF) algorithms to expand the stereo soundfield, making in-ear monitors (IEMs) and headphones sound like an expansive acoustic room.
- **Sub-Bass Exciter (Bass Boost)**: Generates low-frequency psychoacoustic harmonics to give bass impact without causing digital clipping or muddying vocal midrange.

### 2.6 Dual-Column Box Card Preset Management
Presets are organized into an intuitive dashboard:
- **Custom & AI Presets (Top Section)**: AI-generated acoustic profiles and user-created custom profiles are elevated to the top for instant one-tap switching, complete with delete controls.
- **Curated Studio Profiles**: Pre-calibrated factory presets including *Bass Boosted AF, Phonk & Drift, Vocal Clarity Surgeon, Midnight Lofi, Acoustic Warmth, Electronic Pulse, Rock Punch,* and *Flat Reference*.

---

## 3. How It Is Made: Architecture & Tech Stack

SouvikEQ is built strictly following modern Android development best practices, emphasizing clean architecture, reactive state management, and native performance.

### 3.1 Tech Stack Summary
| Layer | Technology | Purpose |
|---|---|---|
| **Language** | Kotlin 2.0 (100%) | Null-safety, coroutines, clean functional syntax |
| **UI Framework** | Jetpack Compose | Declarative UI, reactive recomposition, hardware acceleration |
| **Design System** | Material Design 3 (Material You) | Modern typography, surface containers, dynamic theming |
| **Architecture** | MVVM + Unidirectional Data Flow (UDF) | Predictable state flow via `StateFlow` and Coroutine Scopes |
| **Audio Processing** | Android AudioFX API | Low-latency hardware DSP (`Equalizer`, `Virtualizer`, `BassBoost`) |
| **AI Integration** | RESTful LLM API + Custom Protocol Parser | Conversational intelligence and automated JSON extraction |
| **Speech Recognition**| Android `SpeechRecognizer` + On-Device API | Hands-free voice input with graceful offline fallbacks |
| **Persistence** | Android SharedPreferences + JSON Serialization | Persistent storage of custom presets, active states, and volume |

### 3.2 Architectural Flow
```
┌────────────────────────────────────────────────────────┐
│                   Jetpack Compose UI                   │
│   (EqualizerScreen, StudioFaders, BézierCurve, Visualizer)│
└───────────────────────────▲────────────────────────────┘
                            │ (Observes StateFlow)
                            │ (Dispatches User Events)
┌───────────────────────────┴────────────────────────────┐
│                  EqualizerViewModel                    │
│   - Holds EqualizerUiState (immutably)                 │
│   - Coordinates Audio Engine, AI Engine & Presets      │
└───────────▲───────────────────────────────▲────────────┘
            │                               │
┌───────────┴──────────────┐   ┌───────────┴─────────────┐
│     EqualizerEngine      │   │     AiPresetEngine      │
│  - Equalizer FX          │   │  - System Persona Prompt│
│  - Virtualizer FX        │   │  - Protocol Parsing     │
│  - BassBoost FX          │   │  - LLM REST Backend     │
│  - Session Management    │   │  - VoiceInputManager    │
└──────────────────────────┘   └─────────────────────────┘
```

---

## 4. What Makes SouvikEQ Stand Out: The AI Sound Engineer & Acoustic Intelligence

The defining breakthrough of SouvikEQ is its **AI Sound Engineer**—an intelligent, conversational acoustic specialist integrated directly into the mastering studio. It represents a major paradigm shift in mobile audio software.

### 4.1 The Core Innovation: From Guesswork to Conversational Consultation
In traditional audio software, tuning sound requires understanding parametric filter slopes, Q factors, and frequency cutoffs. When an ordinary listener experiences acoustic issues—such as *“my earbuds sound harsh when guitars kick in”* or *“the bass drowns out the singer in hip-hop tracks”*—they are left helpless.

SouvikEQ replaces complex parameter tweaking with an interactive consultation:
1. **Hardware & Acoustic Discovery**: The AI actively inquires about the listener's specific gear (e.g., bright IEMs, bass-heavy consumer headphones like Sony WH-1000XM4, open-back studio reference cans, or car speakers).
2. **Genre-Specific Diagnostics**: It questions the genre being played (Hip-Hop, Metal, EDM, Jazz, Lo-Fi, Podcasts) and pinpoints specific acoustic shortcomings (muddy low-mids, sibilant 'S' sounds, recessed soundstage).
3. **Psychoacoustic Translation**: The AI translates these subjective descriptions into calibrated frequency curves—applying precise surgical dips at 230 Hz to eliminate boxiness, selective boosts at 3.6 kHz for vocal air, and tuned spatializer levels.

### 4.2 Automated Machine-to-Machine Protocol Engine
The AI Sound Engineer does not just offer text recommendations; it directly interfaces with the Android audio DSP pipeline in real time through an embedded machine protocol.

1. **System Persona & Protocol Instruction**:
   The AI engine is prompted with strict acoustic engineering guidelines and programmed to encapsulate generated presets in a structured, delimited protocol:
   ```
   <<<PRESET_DATA
   {"name":"Vocal Clarity Surgeon","tagline":"Mastered by AI Sound Engineer","bands":[-100,150,450,200,-50],"bassBoost":100,"virtualizer":250}
   PRESET_DATA>>>
   ```

2. **Real-Time Stream Parsing**:
   As the LLM stream arrives, `AiPresetEngine.kt` uses high-efficiency regex extraction:
   ```kotlin
   val PRESET_REGEX = Regex("<<<PRESET_DATA\\s*(\\{.*?\\})\\s*PRESET_DATA>>>", RegexOption.DOT_MATCHES_ALL)
   ```
   The conversational dialogue is preserved for the user to read, while the JSON payload is extracted automatically.

3. **1-Tap Interactive Action Item in Chat**:
   When the parser extracts a valid `AiPresetData` block, the chat UI dynamically injects a distinctive, interactive **"Apply AI Preset"** button directly inside the bot's response bubble.

4. **Instant DSP Injection & Permanent Dashboard Persistence**:
   When the user taps "Apply AI Preset":
   - The 5 frequency band gains (-12 dB to +12 dB scaled to millibels) are applied instantly to the hardware `Equalizer`.
   - The Virtualizer (3D soundstage) and Bass Boost (sub-bass exciter) levels are adjusted immediately without audio dropouts or clicks.
   - The preset is saved permanently into the user's **Custom & AI Presets** collection on the home dashboard with a custom title and tagline (e.g., *“Mastered by AI Sound Engineer”*).

### 4.3 Integrated Hands-Free Voice Input
Tuning your audio while listening to music should be frictionless. With `VoiceInputManager.kt`, users can tap the microphone button to describe what they want hands-free:
- Supports Android 12+ on-device speech recognition (`SpeechRecognizer.createOnDeviceSpeechRecognizer`).
- Includes informative, user-friendly feedback if speech models or permissions are unavailable.

### 4.4 Why This Stands Out in the Audio Industry
- **Subjective-to-Objective Translation**: Bridges the gap between how humans perceive sound (*“make it warmer”*) and how DSP chips work (*-2.5 dB at 230 Hz, +1.8 dB at 14 kHz*).
- **Personalized to Your Specific Headphones**: No two pairs of headphones have the same frequency response; the AI customizes the curve specifically for the listener's exact model.
- **No Complex Setup or Subscriptions**: Built directly into the app with instantaneous preset generation.

---

## 5. Project File Structure Tour

```
app/src/main/java/com/example/myapplication/
├── MainActivity.kt                  # Activity entry point, Edge-to-Edge windowing, permissions
├── ai/
│   ├── AiPresetEngine.kt            # Conversational AI engine, system prompts, protocol parser
│   └── VoiceInputManager.kt         # SpeechRecognizer & on-device voice input manager
├── audio/
│   └── EqualizerEngine.kt           # Low-level AOSP AudioFX wrapper (Equalizer, BassBoost, Virtualizer)
├── receiver/
│   └── AudioSessionReceiver.kt      # BroadcastReceiver intercepting system audio sessions
├── ui/
│   ├── EqualizerScreen.kt           # Main Compose UI, Presets view, EQ mode, AI modal sheet, 3D FX
│   ├── EqualizerViewModel.kt        # StateFlow state holder, user intents, preset persistence
│   ├── EqualizerUiState.kt          # Immutable state definitions & data classes
│   ├── components/
│   │   ├── AudioSpectrumVisualizer.kt  # 32-band reactive spectrum bar visualizer
│   │   ├── ParametricFrequencyCurve.kt # Real-time Cubic Bézier EQ response curve
│   │   └── StudioFaderControl.kt       # Hardware mixing desk vertical fader controls
│   └── theme/
│       ├── Color.kt                 # Obsidian dark, cream bright, and crimson/coral studio palettes
│       ├── Theme.kt                 # Dynamic Material You & custom theme engine
│       └── Type.kt                  # Modern typography definitions
```

---
*Report generated for SouvikEQ – Android Material You Audio Equalizer & AI Acoustic Studio.*
