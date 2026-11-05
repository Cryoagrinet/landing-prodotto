# Regole del progetto

## Git e pubblicazione
- **Mai commit o push diretti su `main`.** `main` è la produzione su Vercel.
- Ogni modifica va su un branch `feat/...` o `fix/...` con una Pull Request verso `main`.
- Il merge lo decide solo l'utente, dopo aver controllato il Preview deployment di Vercel. Non fare mai merge, né attivare auto-merge.
- Mai force push.
- Ogni modifica parte da un nuovo branch con nome descrittivo (es. modifica-hero).
- Prima di proporre una Pull Request, avvia l'anteprima locale e verifica desktop e mobile.
- Spiega in italiano semplice cosa stai facendo nelle operazioni Git

## Tecnologia
- Sito statico: `index.html` alla radice, CSS inline, nessun framework, nessuna build, nessun `vercel.json` se non serve.
- Unica dipendenza esterna: Google Fonts (Outfit).

## Contenuti
- Lingua principale italiano, con riga in inglese.
- Il footer deve riportare ragione sociale, P.IVA e sede legale reali (obbligo di legge in Italia).
