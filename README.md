# Clause

<img width="1305" height="749" alt="Screenshot 2025-11-08 at 8 52 38 PM" src="https://github.com/user-attachments/assets/f0c3e822-f6e7-4d3f-88e3-199c80f626a5" />

Clause is an AI-powered legal enforcement platform. Upload a lease, medical bill, or contract! Our system detects violations, calculates damages, and generates demand letters with statute citations. A Chrome extension flags illegal clauses in real-time on Airbnb listings. Everything is timestamped on Solana's blockchain for tamper-proof evidence in court. Ask questions via voice or text (in any language), and get instant answers grounded in Massachusetts law.

Devpost: [https://devpost.com/software/clause-bu9l74?ref_content=user-portfolio&ref_feature=in_progress](https://devpost.com/software/clause-bu9l74)
Presentation: [https://docs.google.com/presentation/d/1Dk0eTkfH2HfcC2rGY1lnY7-viMub2LUqeJZXiIdstzQ/edit?usp=sharing](https://docs.google.com/presentation/d/1Dk0eTkfH2HfcC2rGY1lnY7-viMub2LUqeJZXiIdstzQ/edit?usp=sharing)

## Quick Start

```bash
# 1. Install dependencies
pip install -r requirements.txt
python -m spacy download en_core_web_sm

# 2. Set up environment variables
# Create .env file with:
GEMINI_API_KEY=your_key
SNOWFLAKE_ACCOUNT=your_account
SNOWFLAKE_USER=your_user
SNOWFLAKE_PASSWORD=your_password
SNOWFLAKE_WAREHOUSE=your_warehouse
SNOWFLAKE_DATABASE=your_database
SNOWFLAKE_SCHEMA=your_schema

# 3. Start the server
cd app
python server.py

# 4. Open the app
# Navigate to: http://localhost:8000/app
# API docs at: http://localhost:8000/docs
```

## Tech Stack

<img width="577" height="594" alt="Screenshot 2025-11-10 at 5 11 24 PM" src="https://github.com/user-attachments/assets/4c89df59-0d02-442d-a850-cd97e865bf18" />

- Frontend: React web app + Chrome extension for real-time scanning
- Backend: FastAPI with PII redaction (spaCy NER + regex) before processing
- RAG Pipeline: Snowflake Cortex (vector embeddings via snowflake-arctic-embed-l-v2.0) + chunked legal documents stored in Snowflake tables
- LLM: Gemini 2.0 Flash Thinking for legal analysis, grounded by retrieved statutes
- Voice Chat: ElevenLabs
- Blockchain: Solana for immutable document hashing + future escrow/reputation features
- Storage: Cloudflare R2 for documents, Solana for metadata
- Deployment: Vultr Cloud hosting
