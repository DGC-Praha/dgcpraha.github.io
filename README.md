# DGCP website

Web Disc Golf Clubu Praha — [dgcp.cz](https://dgcp.cz)

---

## Editace přes GitHub (bez instalace)

Pro jednoduché úpravy obsahu stránek nepotřebujete nic instalovat. Stačí webový prohlížeč a účet na GitHubu.

### Kde najdu soubory k editaci

Veškeré stránky webu se nacházejí ve složce [`src/pages/`](https://github.com/dgcpraha/dgcpraha.github.io/tree/master/src/pages):

| Soubor | Stránka |
|--------|---------|
| `src/pages/index.html` | Hlavní stránka |
| `src/pages/krouzek.html` | Kroužek discgolfu |
| `src/pages/nase_turnaje.html` | Pořádané ligy a turnaje |
| `src/pages/instrukce_slevy.html` | Jak uplatnit slevy u partnerů |
| `src/pages/seznam_clenu.html` | Seznam členů |
| `src/pages/navrhni-dres.html` | Soutěž o návrh dresu |

Sdílené části webu (navigace, patička) jsou ve složce [`src/partials/`](https://github.com/dgcpraha/dgcpraha.github.io/tree/master/src/partials):

| Soubor | Co obsahuje |
|--------|-------------|
| `src/partials/nav.html` | Navigační menu (zobrazuje se na všech stránkách) |
| `src/partials/footer.html` | Patička se sociálními sítěmi a copyrightem |
| `src/partials/head.html` | Hlavička stránky (CSS, fonty) |
| `src/partials/scripts.html` | Importy JavaScriptu |

### Jak provést úpravu

1. Přihlaste se na [GitHub](https://github.com)
2. Otevřete soubor, který chcete upravit (viz tabulky výše)
3. Klikněte na ikonku tužky ("Edit this file") vpravo nahoře
4. Proveďte úpravy v textu — měníte jen obsah mezi HTML tagy, např. text mezi `<p>` a `</p>`
5. Dole v části "Commit changes" stručně popište, co jste změnili
6. Zvolte "Create a new branch" a klikněte na "Propose changes"
7. Na další stránce klikněte "Create pull request"
8. Požádejte správce, aby změny zkontroloval, spustil build a schválil

### Důležité

- **Needitujte HTML soubory v kořenovém adresáři** (např. `index.html`, `krouzek.html`) — ty jsou generované a vaše změny by se při dalším buildu přepsaly. Vždy editujte soubory ve složce `src/`.
- Pokud chcete změnit navigaci nebo patičku, stačí upravit příslušný soubor v `src/partials/` — změna se projeví na všech stránkách najednou.

---

## Lokální vývoj (pro vývojáře)

### Požadavky

- [Node.js](https://nodejs.org/) (viz `.nvmrc` pro doporučenou verzi)
- npm (součást Node.js)

### Instalace

```bash
git clone https://github.com/dgcpraha/dgcpraha.github.io.git
cd dgcpraha.github.io
npm install
```

### Vývoj s live reload

```bash
npm start
```

Otevře se prohlížeč na `localhost:3000`. Při uložení jakéhokoli souboru v `src/`, `scss/` nebo `js/` se stránka automaticky obnoví.

### Struktura projektu

```
├── src/                    # ZDROJOVÉ SOUBORY — editujte ZDE
│   ├── pages/              # Obsah jednotlivých stránek
│   │   ├── index.html
│   │   ├── krouzek.html
│   │   ├── nase_turnaje.html
│   │   └── ...
│   └── partials/           # Sdílené komponenty (navigace, patička, ...)
├── scss/                   # Styly (SCSS)
├── js/                     # JavaScript
├── img/                    # Obrázky
├── index.html              # Generované — needitovat!
├── krouzek.html            # Generované — needitovat!
└── ...
```

Web používá šablonovací systém [gulp-file-include](https://www.npmjs.com/package/gulp-file-include). Stránky v `src/pages/` obsahují pouze unikátní obsah a volání `@@include()` pro sdílené části. Gulp task `html` z nich vygeneruje finální HTML soubory v kořenovém adresáři.

### Gulp tasky

| Příkaz | Co dělá |
|--------|---------|
| `npx gulp` | Buildne vše (HTML + CSS + JS + vendor) |
| `npx gulp html` | Zkompiluje HTML šablony ze `src/` |
| `npx gulp css` | Zkompiluje SCSS do CSS a minifikuje |
| `npx gulp js` | Minifikuje JavaScript |
| `npx gulp watch` | BrowserSync s live reload |

### Workflow pro změny

1. Upravte soubory v `src/pages/` nebo `src/partials/`
2. Spusťte `npx gulp html` (nebo `npx gulp` pro kompletní build)
3. Commitněte jak zdrojové soubory (`src/`), tak vygenerované HTML
4. Pushněte a vytvořte pull request

## Licence

[MIT](https://github.com/BlackrockDigital/startbootstrap-agency/blob/gh-pages/LICENSE)
