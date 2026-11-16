# Guida al flusso di deploy

## I tre livelli

| Branch | A cosa serve | Indirizzo | Chi lo vede |
| --- | --- | --- | --- |
| `nome-modifica` (es. `modifica-hero`) | una singola modifica in lavorazione | Preview della PR (link nel commento Vercel) | solo il team Vercel |
| `staging` | anteprima stabile di ciò che sta per andare online | `landing-prodotto-git-staging-cryo-agri-net.vercel.app` (poi `staging.cryoagrinet.it`) | solo il team Vercel, o chi ha uno Share link |
| `main` | **produzione**, il sito pubblico | dominio di produzione | tutti |

`staging` e `main` sono permanenti: **non cancellarli mai**, nemmeno quando GitHub propone "Delete branch" dopo un merge da `staging` verso `main`.

## Il giro di una modifica

**① Modifica** (Claude)
Claude crea un branch da `staging`, fa la modifica, la verifica in locale su desktop e mobile e apre una **PR verso `staging`**.

**② Controllo della singola modifica** (tu, facoltativo)
Nella PR, il commento del bot Vercel → link **Preview**. Utile per modifiche grandi; per quelle piccole puoi passare subito al punto ③.

**③ Merge in staging** (tu)
Nella PR → freccia ▾ → **Squash and merge** → **Confirm** → **Delete branch** (qui sì: è il branch della singola modifica).

**④ Controllo su staging** (tu)
Apri l'indirizzo di staging: dopo circa un minuto mostra la nuova versione. Controlla desktop e mobile. Per farlo vedere a qualcuno: barra Vercel in basso → **Share**, oppure dalla dashboard Vercel → deployment → **Share**.

**⑤ Richiesta di pubblicazione** (Claude, o tu)
Si apre una **PR da `staging` verso `main`**. Puoi chiederla a Claude ("apri la PR di rilascio"), oppure crearla tu su GitHub: **Pull requests → New pull request**, con base `main` e compare `staging`.

**⑥ Pubblicazione** (tu)
Nella PR di rilascio → freccia ▾ → **Create a merge commit** → **Confirm**.
⚠️ Qui **non** usare Squash: `staging` e `main` resterebbero disallineati e ogni rilascio successivo riproporrebbe vecchie modifiche.
⚠️ **Non** cliccare "Delete branch".

**⑦ Verifica in produzione** (tu)
vercel.com → progetto `landing-prodotto` → **Deployments**: l'ultimo deve essere *Production* e *Ready*. Poi apri il sito pubblico.

## Promemoria veloce

- Modifica → staging: **Squash and merge** + Delete branch
- Staging → main: **Create a merge commit**, senza Delete branch
- Il merge lo fai sempre tu: Claude prepara, tu approvi.

## Operazioni una tantum su Vercel (manuali)

1. **Dominio di staging** (facoltativo): Settings → **Domains** → *Add* → `staging.cryoagrinet.it` → nel campo **Git Branch** scegli `staging` → salva. Poi, dal pannello del tuo registrar del dominio, aggiungi il record DNS che Vercel indica (di solito `CNAME staging → cname.vercel-dns.com`).
2. **Dominio di produzione**: Settings → **Domains** → *Add* → `cryoagrinet.it` (e `www.cryoagrinet.it`) senza branch, quindi collegato a `main` → record DNS indicati da Vercel.
3. **Protezione**: Settings → **Deployment Protection** → verifica che **Vercel Authentication** sia attiva (*Standard Protection*). Protegge Preview e staging, mentre la produzione resta pubblica.
4. **Branch di produzione**: Settings → **Git** → *Production Branch* deve essere `main`.
