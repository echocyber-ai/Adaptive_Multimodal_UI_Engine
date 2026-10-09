# Adaptive Multimodal UI Engine (Sugar & Crumb)

An interactive Human-Computer Interaction (HCI) prototype demonstrating **adaptive, multimodal user interfaces**. The application dynamically reconfigures its visual hierarchy, target sizes, focus states, and input processing pipelines based on the active interaction modality: **Touch, Mouse/Fine Pointer, Keyboard, Voice (Speech-in / Speech-out)**, and **Direct Manipulation Gestures**.

---

## Key HCI Concepts Demonstrated

### 1. Dynamic Modality Detection & Adaptive Layouts
- **Touch / Coarse Pointer:** Enlarges hit targets (`--btn-padding`, `--btn-font-size`) to mitigate Fitts's Law constraints on touch devices.
- **Keyboard Navigation:** Activates persistent, high-contrast focus rings (`body.mode-keyboard`) and enables complete keyboard-only manipulation of the workspace.
- **Fine Pointer (Mouse):** Implements magnetic UI snaps, dynamic cursor scaling, and ambient spatial illumination.
- **Voice Control:** Expands contextual awareness displays, activates microphone status indicators, and handles hands-free task execution.

### 2. Multimodal Input Fusion & Redundancy (Equifinality)
Users can accomplish identical goals (e.g., customizing, resizing, and filtering products) via multiple distinct or combined modalities:
- **Speech Recognition (`Web Speech API`):** Natural language parsing for flavor selection, topping toggles, size changes, and catalog queries.
- **Direct Manipulation & Inertial Physics:** Pointer-event drag-and-throw mechanics with velocity-based glide and collision bounding.
- **Visual Feedback & Ambient Affordances:** Real-time spatial tracking, 3D card tilt, particle burst reactions, and screen-zone color shifts.

### 3. Accessible Conversational Output (Speech Synthesis)
- Bidirectional conversational agent with an interactive avatar speech bubble and synthetic speech response (`SpeechSynthesisUtterance`).
- Automatic collision avoidance between input and output audio (pauses speech recognition while the system speaks to prevent self-triggering loops).

---

## Features & Interaction Modes

| Modality | Controls / Gestures | System Response |
| :--- | :--- | :--- |
| **Voice (Speech)** | Press `M` or tap 🎤<br>Say: *"chocolate base"*, *"sprinkles"*, *"bigger"*, *"spin"*, *"search strawberry"* | Real-time speech recognition parses intent, mutates SVG state, logs dialog, and triggers synthesized vocal confirmation. |
| **Direct Gesture** | Pointer Drag & Flick | Direct manipulation of the canvas artifact; flicking applies velocity and frictional decay (`requestAnimationFrame`). |
| **Mouse / Pointer** | Cursor movement across canvas, scroll wheel on stage | Parallax sprinkle drift, cursor aura scaling, 3D card perspective tilt, and wheel-based zoom scaling. |
| **Keyboard** | <kbd>Tab</kbd>, Arrow keys (<kbd>←</kbd> <kbd>→</kbd> <kbd>↑</kbd> <kbd>↓</kbd>), <kbd>+</kbd> / <kbd>-</kbd>, <kbd>0</kbd> (reset), <kbd>M</kbd> | Focus indicators activate; full discrete control of canvas elements without pointer requirements. |
| **GUI Panels** | Categorized chip trays (Base, Frosting, Toppings, Size) | Direct click/tap state updates with dynamic ARIA attribute toggling (`aria-pressed`, `aria-expanded`). |

---

## Technical Stack

- **Markup & Vector Graphics:** Semantic HTML5, Embedded SVG manipulation (`defs`, `symbols`, dynamic transforms).
- **Styling:** Vanilla CSS3 (Custom properties / CSS variables, hardware-accelerated transforms, `@media (prefers-reduced-motion)` fallbacks).
- **APIs:** 
  - Web Speech API (`SpeechRecognition` / `webkitSpeechRecognition`)
  - Web Speech Synthesis API (`speechSynthesis`)
  - Pointer Events API (Unified mouse/touch drag capture)
- **Architecture:** Zero-dependency, standalone single-file client-side implementation.

---

## Getting Started

### Prerequisites
- Modern Chromium-based browser (**Google Chrome** or **Microsoft Edge** recommended for native Web Speech Recognition support).
- Microphone access (required for voice commands).

### Running Locally
1. Clone or download the repository:
   ```bash
   git clone [https://github.com/your-username/adaptive-multimodal-ui-engine.git](https://github.com/your-username/adaptive-multimodal-ui-engine.git)
   cd adaptive-multimodal-ui-engine
