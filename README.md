# DGCP website

Web Disc Golf Clubu Praha. Založeno na [Agency](https://startbootstrap.com/template-overviews/agency/) šabloně od Start Bootstrap.

## Struktura projektu

```
dgcp-web/
├── src/                    # ZDROJOVÉ SOUBORY — editujte ZDE
│   ├── pages/              # Zdrojové stránky (obsah jednotlivých stránek)
│   │   ├── index.html
│   │   ├── krouzek.html
│   │   ├── nase_turnaje.html
│   │   ├── instrukce_slevy.html
│   │   ├── seznam_clenu.html
│   │   ├── navrhni-dres.html
│   │   └── scitani/        # Stránky návštěvnosti hřišť
│   └── partials/           # Sdílené komponenty
│       ├── head.html       # <head> blok (meta tagy, CSS, fonty)
│       ├── nav.html        # Navigační menu
│       ├── footer.html     # Patička (sociální sítě, copyright)
│       └── scripts.html    # JS importy (jQuery, Bootstrap, agency.js)
├── scss/                   # SCSS styly
├── css/                    # Zkompilované CSS (generováno z SCSS)
├── js/                     # JavaScript
├── img/                    # Obrázky
├── vendor/                 # Závislosti třetích stran (generováno z node_modules)
├── index.html              # GENEROVANÉ — needitovat přímo!
├── krouzek.html            # GENEROVANÉ
├── ...                     # (další generované HTML soubory)
└── scitani/                # GENEROVANÉ
```

## Jak to funguje

Web používá šablonovací systém `gulp-file-include`. Zdrojové stránky v `src/pages/` obsahují pouze unikátní obsah každé stránky a volání `@@include()` pro sdílené části (navigace, patička atd.). Gulp task `html` zkompiluje šablony a vygeneruje finální HTML soubory v kořenovém adresáři, které se pak zobrazují na webu.

**HTML soubory v kořenovém adresáři jsou generované — needitujte je přímo!** Při dalším buildu by se vaše změny přepsaly.

## Editace webu

### Úprava obsahu stránky
Editujte odpovídající soubor v `src/pages/`, např. `src/pages/krouzek.html`.

### Úprava navigace, patičky nebo hlavičky
Editujte soubor v `src/partials/` — změna se automaticky projeví na všech stránkách.

### Úprava stylů
Editujte SCSS soubory ve složce `scss/`.

### Po úpravě
Spusťte build pro vygenerování finálních souborů:
```bash
npx gulp html        # pouze HTML
npx gulp build       # vše (HTML + CSS + JS + vendor)
```

Commitněte jak zdrojové soubory (`src/`), tak vygenerované HTML soubory.

## Editace pro mírně pokročilé (přes GitHub)

Pokud chcete upravit pouze obsah jedné stránky:

1. Přihlaste se na GitHub
2. Otevřete odpovídající soubor ve složce `src/pages/` v repozitáři [dgcpraha/dgcpraha.github.io](https://github.com/dgcpraha/dgcpraha.github.io)
3. Stiskněte tlačítko "Edit this file" (ikonka tužky)
4. Proveďte úpravy
5. Dole v části "Commit changes" stručně popište svoji úpravu
6. Stiskněte "Propose file change" a poté "Create pull request"
7. Požádejte někoho ze správců, aby změny potvrdil a spustil build

## Vývoj

### Požadavky
- Node.js (viz `.nvmrc` pro doporučenou verzi)
- npm

### Instalace
```bash
npm install
```

### Vývoj s live reload
```bash
npm start
```
Otevře se prohlížeč na `localhost:3000`, který se automaticky obnovuje při změnách.

### Gulp tasky
- `gulp` — výchozí task, buildne vše
- `gulp watch` — BrowserSync s live reload
- `gulp html` — zkompiluje HTML šablony ze `src/` do kořenového adresáře
- `gulp css` — zkompiluje SCSS do CSS a minifikuje
- `gulp js` — minifikuje JS
- `gulp vendor` — zkopíruje závislosti z node_modules do vendor/

## Licence

[MIT](https://github.com/BlackrockDigital/startbootstrap-agency/blob/gh-pages/LICENSE)
