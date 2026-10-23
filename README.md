# 🧑‍💻 AI Code Explainer & Reviewer

Paste or upload code and get an explanation, a severity-tagged code review, an improved version, and answers to your own questions. Built with **Streamlit** and **Google Gemini Flash**.

## Features
- Paste code or upload a file (Python, JS, Java, C/C++, Go, Rust, SQL and more)
- Choose what you want: explanation, review, improved version
- Pick review focus: bugs, security, performance, style, best practices, testing
- Ask a specific question about the code
- Streaming responses and a download button for the result (.md)

## Project structure
```
.
├── app.py             # Streamlit app
├── requirements.txt   # Dependencies
└── README.md
```

## Run locally
1. Get a free API key at https://aistudio.google.com/apikey
2. Install and run:
   ```bash
   python -m venv venv
   source venv/bin/activate        # Windows: venv\Scripts\activate
   pip install -r requirements.txt
   export GEMINI_API_KEY="your_key" # Windows PowerShell: $env:GEMINI_API_KEY="your_key"
   streamlit run app.py
   ```
   You can also paste the key into the sidebar instead of setting the variable.

## Configure the API key (recommended: secrets)
Create `.streamlit/secrets.toml` (never commit it):
```toml
GEMINI_API_KEY = "your_key"
```
Add this to `.gitignore`:
```
.streamlit/secrets.toml
venv/
__pycache__/
```

## Push to GitHub
```bash
git init
git add app.py requirements.txt README.md .gitignore
git commit -m "Initial commit: AI code reviewer"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

## Deploy on Streamlit Community Cloud (free)
1. Go to https://share.streamlit.io and sign in with GitHub.
2. Click **Create app**, pick your repo, branch `main`, main file `app.py`.
3. Open **Advanced settings → Secrets** and add:
   ```toml
   GEMINI_API_KEY = "your_key"
   ```
4. Click **Deploy**. Your app gets a public URL.

## Notes
- Default model is `gemini-2.5-flash`; change it in the sidebar if Google updates model names.
- Input is limited to 30,000 characters.
- Code you submit is sent to Google's Gemini API, so don't paste secrets or private code you aren't allowed to share.
