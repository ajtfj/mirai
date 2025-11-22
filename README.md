# Mirai - Interactive AI Video Storytelling

Mirai is an platform for generating interactive video stories where the narrative adapts dynamically to user decisions. Leveraging the power of Generative AI, the system creates scripts, voiceovers, sound effects, and images in real-time to build an immersive, branching audiovisual experience.

## About the Project

The core goal of Mirai is to allow users to co-author visual stories. At key narrative moments, the user makes a decision using natural language. The system processes this choice and automatically generates the continuation of the story—not just as text, but as a complete video with narration, character dialogue, and ambient soundtracks.

## Key Features

- **Branching Narrative:** Create non-linear stories where every decision spawns a new branch in the story tree.
- **Natural Language Decisions:** You are not limited to pre-defined options; type freely what your character should do.
- **Automatic Video Generation:**
  - **Scripting:** Narrative and dialogue generation via LLMs (OpenAI GPT-4o).
  - **Visuals:** Consistent image generation for every scene (Together AI / Flux).
  - **Audio:** Voice synthesis for narrator and characters (ElevenLabs/OpenAI) and AI-generated ambient sound effects.
  - **Assembly:** Automatic video and audio editing and concatenation (MoviePy).
- **Visual Navigation:** Interactive "Story Tree" interface to visualize and navigate between different paths and timelines.
- **Multi-Genre:** Support for various literary genres (Fantasy, Sci-Fi, Mystery, Horror, etc.).
- **Story Management:** Save your progress and resume previous stories from where you left off.

## Technology Stack

### Backend (API)

- Python 3.12
- **FastAPI:** High-performance web framework.
- **MongoDB & Motor:** NoSQL database for storing users, story metadata, and decision tree structures.
- **MoviePy:** Programmatic video processing and editing.

### AI Services

- **OpenAI API:** Text generation (GPT-4o), Transcription (Whisper), and TTS.
- **ElevenLabs:** Advanced voice synthesis for distinct characters.
- **Together AI:** Image generation (Flux Model).

### Frontend (UI)

- React 18 (with Vite)
- TypeScript
- **Tailwind CSS:** Responsive styling.
- **Zustand:** Global state management.
- **React D3 Tree:** Visualization of the story navigation tree.

### Infrastructure

- Docker & Docker Compose: Container orchestration for easy development and deployment.
- Google OAuth: User authentication.

---

## Getting Started

### Prerequisites

- Docker and Docker Compose installed.
- API Keys for external services (OpenAI, ElevenLabs, Together AI).
- Google Cloud Credentials (Client ID) for authentication.

### Environment Configuration

Create a `.env` file in the project root (or configure variables in your environment/docker-compose.yml) with the following keys:

```env

# Database

MONGODB_USERNAME=admin

MONGODB_PASSWORD=password123

# AI APIs

OPENAI_API_KEY=sk-...

ELEVENLABS_API_KEY=...

TOGETHER_API_KEY=...

# Authentication

JWT_SECRET=your_super_secure_jwt_secret

GOOGLE_CLIENT_ID=your_google_client_id.apps.googleusercontent.com

# Frontend Configuration (for UI build)

VITE_API_URL=http://localhost:8000

VITE_HOST=0.0.0.0

VITE_PORT=5173

VITE_GOOGLE_CLIENT_ID=your_google_client_id.apps.googleusercontent.com

```

### Installation & Running

Clone the repository:
```bash

git clone https://github.com/your-username/mirai.git

cd mirai

```

Start services with Docker Compose (the command below will build the API and UI images and start MongoDB):

```bash

make watch

# Or alternatively:

docker compose up --build

```

Access the Application:
- **Frontend:** http://localhost:5173  

- **API Docs (Swagger):** http://localhost:8000/docs

---

## How to Use

1. Log in with your Google account.

2. Click **"Create New Story"** and select a genre (e.g., Fantasy, Cyberpunk).

3. Wait while the AI generates the video introduction for your story.

4. Watch the video. At the end, a text box will appear.

5. Type your decision (e.g., "I pick up the sword and enter the cave" or "I try to negotiate with the guard").

6. The system will generate the next chapter based on your choice.

7. Use the **Tree** button in the player to visualize branches and revisit previous points to make different decisions.

---

##  Repository Structure

```text

mirai/
├── api/                 # Backend Source Code (FastAPI)
│   ├── audio/           # Audio processing and effects
│   ├── audiovisual/     # Orchestration of Audio+Visual assembly
│   ├── auth/            # Authentication logic (JWT, Google OAuth)
│   ├── common/          # Shared models and utilities
│   ├── database/        # MongoDB connection and configuration
│   ├── script/          # Narrative generation logic
│   ├── story/           # Core story state and tree management
│   ├── stt/             # Speech-to-Text
│   ├── tti/             # Text-to-Image
│   ├── tts/             # Text-to-Speech
│   ├── ttt/             # Text-to-Text 
│   ├── user/            # User management services
│   ├── visual/          # Visual asset management
│   └── video/           # Final video generation and streaming
├── ui/                  # Frontend Source Code (React)
│   ├── src/
│   │   ├── components/  # React Components (Player, Tree, etc.)
│   │   ├── services/    # API communication
│   │   └── store/       # State management (Zustand)
└── docker-compose.yml   # Container orchestration

```
---

## Contributing



Contributions are welcome! Feel free to open issues or submit pull requests to improve story generation, add new visual styles, or optimize the interface.
