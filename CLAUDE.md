# Regole del progetto

## Git e pubblicazione
- **Mai commit o push diretti su `main` né su `staging`.** `main` è la produzione su Vercel; `staging` è l'anteprima stabile (`landing-prodotto-git-staging-cryo-agri-net.vercel.app`).
- Ogni modifica parte da un nuovo branch creato da `staging`, con nome descrittivo (es. modifica-hero), e va in una Pull Request verso `staging`.
- Per pubblicare, aprire una Pull Request da `staging` verso `main` (la "PR di rilascio") solo quando l'utente lo chiede.
- Il merge lo decide solo l'utente, dopo aver controllato l'anteprima. Non fare mai merge, né attivare auto-merge. Mai cancellare i branch `staging` e `main`.
- Mai force push.
- Flusso completo in `GUIDA-DEPLOY.md`: tenerla aggiornata se il flusso cambia.
- Prima di proporre una Pull Request, avvia l'anteprima locale e verifica desktop e mobile.
- Spiega in italiano semplice cosa stai facendo nelle operazioni Git

## Tecnologia
- Sito statico: `index.html` alla radice, CSS inline, nessun framework, nessuna build, nessun `vercel.json` se non serve.
- Unica dipendenza esterna: Google Fonts (Outfit).

## Contenuti
- Sito bilingue: italiano per browser in italiano, inglese per gli altri; selettore IT | EN senza salvataggio della scelta. I testi inglesi sono nello script in fondo a `index.html`.
- Il footer riporta ragione sociale e P.IVA: Cryoagrinet Società Agricola S.R.L. · P.IVA 04617550712.
