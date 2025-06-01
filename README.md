# MOM-Generator
# 📋 Meeting Minutes Assistant

Turn any public YouTube video into clear, structured meeting minutes with one REST call.

---

## ✨ Key Features
- **Automatic transcript retrieval** &nbsp;•&nbsp; pulls captions directly from YouTube
- **LLM powered summarization** &nbsp;•&nbsp; uses Marvin + OpenAI to extract the who, what, and next steps
- **Structured output** &nbsp;•&nbsp; groups members present, decisions taken, tasks assigned, proposals, challenges, and other points
- **FastAPI backend** &nbsp;•&nbsp; production ready with Pydantic validation and Uvicorn server
- **Single endpoint** &nbsp;•&nbsp; `/summarize/` accepts a video URL and returns JSON minutes

---

## 🏗️ Tech Stack
| Layer      | Libraries / Services |
|------------|----------------------|
| Language Model | Marvin `@ai_fn` + OpenAI GPT |
| Transcript Fetching | `youtube-transcript-api` |
| API Framework | FastAPI & Uvicorn |
| Validation | Pydantic |
| Config | `python-dotenv` |

---

## 🚀 Quick Start

1. **Clone and install**

   ```bash
   git clone https://github.com/<your-handle>/meeting-minutes-assistant.git
   cd meeting-minutes-assistant
   python -m venv .venv
   source .venv/bin/activate          # On Windows use .venv\Scripts\activate
   pip install -r requirements.txt
'
2.Add your OpenAI key

Create a .env file in the project root:
OPENAI_API_KEY=sk-...your-key...

3. Run the server

uvicorn app:app --host 0.0.0.0 --port 8000 --reload

4. Call the endpoint

curl -X POST http://localhost:8000/summarize/ \
  -H "Content-Type: application/json" \
  -d '{"url": "https://www.youtube.com/watch?v=dQw4w9WgXcQ"}'
  
Example response:

{
  "summary": {
    "members_presenting": ["Rick Astley"],
    "important_decisions": ["Never gonna give you up"],
    "tasks_assigned": [],
    "proposals_presented": [],
    "issues_and_challenges": [],
    "other_points": ["Delivered in a catchy tune"]
  }
}

