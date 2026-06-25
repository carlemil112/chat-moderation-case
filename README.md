# Chat Room Monitoring — Case løsning

Løsning til CEGO's Data Intelligence case om automatisk moderation af chatrum.

## Indhold
- Syntetisk datasætgenerering via Anthropic API
- Datasætoverblik og visualiseringer  
- LLM-baseret klassifikationssystem med handlingslogik
- Baseline model (TF-IDF + Logistisk Regression)
- Performance evaluering og sammenligning

## Kørsel
1. Installer dependencies: `pip install anthropic pandas matplotlib scikit-learn python-dotenv`
2. Opret `.env` fil med `ANTHROPIC_API_KEY=din-nøgle`
3. Kør notebook i rækkefølge: `cego_chat_monitoring.ipynb`