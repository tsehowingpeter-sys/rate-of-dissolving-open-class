# Exp 2.5: Factors Affecting Rate of Dissolving
## 影響溶解速率的因素 • AI 賦能科學探究與課堂實時診斷平台

A real-time interactive inquiry web platform designed for S1 Integrated Science Open Classes.

### 🌟 Key Features
- **Agent Water (水精靈) AI Socratic Buddy**:
  - 4 Diverse Thinking Perspectives per dialogue round (🎯 High Scientific Rigor, 🎈 Childish Subjective, ⚠️ Common Misconception, 🔍 Critical Inquiry).
  - Dynamic keyword analysis for free-text input (stirring speed, stopwatch reaction delay, STEM sensors, etc.).
  - Personalized Key Learning Points Summary card with yellow border.
- **Teacher Command Center (`teacherwater`)**:
  - Custom Class Name Switcher (`Class 1A`, `1B`, etc.) with independent namespaces.
  - Non-destructive Auto-fill (preserves existing student data).
  - Synchronized Class Comparison Graph and 8 Groups Overview table for projector display.
  - Bilingual Whole-Class Discussion Prompts with collapsible scaffolding questions.
- **Real-Time Cross-Device Synchronization**:
  - MQTT over WebSocket (`wss://broker.emqx.io:8084/mqtt`) + BroadcastChannel + LocalStorage.
