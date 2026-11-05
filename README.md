# CryoAgriNet – Landing page

Pagina "coming soon" di CryoAgriNet. Sito **statico**: un solo `index.html` con CSS inline, senza framework e senza build.

## Vedere la pagina in locale

Apri `index.html` con un doppio clic nel browser.

## Flusso di lavoro

`main` = **produzione**: tutto ciò che arriva su `main` viene pubblicato da Vercel.

1. Ogni modifica si fa su un branch (`feat/...` per novità, `fix/...` per correzioni).
2. Si apre una Pull Request verso `main`.
3. Vercel crea un **Preview deployment** (URL di staging non pubblico, protetto dal login Vercel).
4. Si controlla la Preview su desktop e mobile.
5. Solo dopo l'approvazione si fa il merge su `main` → pubblicazione in produzione.

Mai commit o push diretti su `main`.

## Deploy su Vercel

- vercel.com → **Add New → Project** → importa `Cryoagrinet/landing-prodotto`.
- Framework preset: **Other**. Nessun build command, nessuna output directory: Vercel serve i file della radice.
