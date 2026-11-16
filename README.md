# CryoAgriNet – Landing page

Pagina "coming soon" di CryoAgriNet. Sito **statico**: un solo `index.html` con CSS inline, senza framework e senza build.

## Vedere la pagina in locale

Apri `index.html` con un doppio clic nel browser.

## Flusso di lavoro

`modifica` → PR verso **`staging`** (anteprima stabile) → PR **`staging` → `main`** (**produzione**).

Mai commit o push diretti su `main` o su `staging`. Passaggi completi e operazioni manuali in **[GUIDA-DEPLOY.md](GUIDA-DEPLOY.md)**.

## Deploy su Vercel

- vercel.com → **Add New → Project** → importa `Cryoagrinet/landing-prodotto`.
- Framework preset: **Other**. Nessun build command, nessuna output directory: Vercel serve i file della radice.
