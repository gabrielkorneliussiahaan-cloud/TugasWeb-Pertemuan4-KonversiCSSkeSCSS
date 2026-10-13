# Tugas Rutin 4 — Konversi CSS ke SCSS (7-1 Pattern)

Konversi dari `styles.css` Tugas Rutin 2 (Portofolio dark/tech) ke SCSS
modular memakai struktur **7-1 pattern**.

## Struktur folder

```
scss/
├── abstracts/
│   ├── _variables.scss   -> semua warna, spacing, font, breakpoint, map tema
│   └── _mixins.scss      -> 4 mixin reusable
├── vendors/
│   └── _placeholder.scss -> tempat override library pihak ketiga (kosong)
├── base/
│   ├── _reset.scss       -> box-sizing, reset dasar
│   └── _typography.scss  -> link, focus state, class .mono
├── layout/
│   ├── _header.scss      -> navbar + nav list
│   ├── _grid.scss        -> CSS Grid utama (sidebar + main), mobile-first
│   └── _footer.scss
├── components/
│   ├── _buttons.scss
│   ├── _terminal.scss
│   ├── _profile-panel.scss
│   ├── _stat-contact.scss
│   └── _content-blocks.scss  -> json-block, log-list, achievement-list, comment-block
├── pages/
│   └── _home.scss        -> section, reveal animation, print styles
├── themes/
│   └── _dark.scss        -> custom properties warna + dark mode
└── main.scss              -> entry point, @use semua partial
```

## Cara memenuhi tiap ketentuan

| Ketentuan | Lokasi |
|---|---|
| Konversi CSS existing ke SCSS | Seluruh isi `styles.css` Tugas 2 dipindah ke partial-partial di atas |
| Variables untuk colors & spacing | `abstracts/_variables.scss` ($color-*, $space-*, $radius-*) |
| Nesting maks. 3 level | Ditandai komentar `// level 1/2/3` di tiap partial |
| Minimal 3 mixins reusable | `abstracts/_mixins.scss` — ada 4: `respond-to`, `flex-row`, `card-surface`, `hover-lift` |
| Struktur 7-1 pattern | 7 folder: abstracts, vendors, base, layout, components, pages, themes |
| `@use` (bukan `@import`) | Semua partial pakai `@use`, tidak ada `@import` sama sekali |
| Minimal 1 `@each`/`@for` | `themes/_dark.scss` (generate custom property warna) dan `components/_content-blocks.scss` (generate modifier `.log-list__item--*`) |
| Compile pakai Vite/Dart Sass | Sudah dicompile pakai **Dart Sass CLI**, hasilnya ada di `dist/styles.css` |

## Cara compile ulang

Perlu Node.js terpasang, lalu:

```bash
npm install
npm run build      # compile sekali
npm run watch       # compile otomatis setiap ada perubahan
```

`dist/styles.css` adalah hasil compile yang sudah diverifikasi identik
secara visual dengan `styles.css` asli dari Tugas Rutin 2 — cukup ganti
tautan `<link rel="stylesheet" href="styles.css">` di `index.html`
Tugas 2 menjadi `href="dist/styles.css"` (atau salin isinya) untuk
memakainya.
