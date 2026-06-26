# Chat Room Monitoring - Case løsning

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

## Hovedfund

Begge modeller evalueres på samme stratificerede testsæt for en fair sammenligning.

- **LLM** fanger næsten al problematisk adfærd (recall 0.97) men overflager normale 
  beskeder (recall normal 0.12) - høj sensitivitet, mange false positives.
- **Baseline** er konservativ og præcis, men misser næsten halvdelen af de 
  problematiske beskeder (recall 0.52).

5-klasse accuracy er misvisende fordi formatet er strukturelt skævt mod LLM'en 
(den kan ikke producere labelet "edge_case"). Den **binære evaluering** 
(problematisk vs. normal) er derfor den retfærdige sammenligning - den måler det 
produktionen kræver: bliver problematisk adfærd fanget overhovedet?

Valg af model afhænger af kategori: for ludomani vejer en overset sag tungt 
(LLM's recall er bedre), for grimt sprog koster false positives kundetillid 
(baseline's precision er bedre).
