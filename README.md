# 9drive-lp

Landing page untuk [9Drive](https://github.com/namasaiaicat/9drive-drived) — self-hosted Google Drive alternative.

Repo ini berisi **hanya** landing page. Kode aplikasi (backend, frontend, CLI) ada di repo
[9drive](https://github.com/namasaiaicat/9drive-drived).

## Stack

- [Astro 5](https://astro.build) static output
- React 19 via `@astrojs/react`, dipakai hanya untuk islands yang butuh interaksi
- TypeScript, Vitest, Playwright

## Struktur

| Path | Isi |
|---|---|
| `src/pages/index.astro` | Redirect locale: baca `localStorage` → `navigator.language` → `/en` atau `/id` |
| `src/pages/{en,id}/index.astro` | Halaman utama per locale |
| `src/components/` | Komponen Astro statis: `Navbar`, `Hero`, `Features`, `Footer`, `HeadMeta` |
| `src/islands/` | Islands React: `ThemeToggle`, `LanguageSelector`, `MobileDrawer`, `FaqAccordion`, `QuickstartSnippets`, `ShowcaseGallery` |
| `src/data/locales/` | Dictionary `en.ts` dan `id.ts`, ditipe oleh `src/types` |
| `src/styles/` | CSS per section, token warna di `theme.css` |
| `src/utils/` | `locale-router`, `platform-detect`, `scroll`, `storage` |
| `test/` | Unit test Vitest |
| `e2e/` | E2E Playwright (routing, accessibility, FOIT) |

## Menjalankan

```bash
npm install
npm run dev        # dev server, http://localhost:4321
npm run build      # output statis ke dist/
npm run preview    # serve hasil build
```

## Verifikasi

```bash
npm run lint        # tsc --noEmit
npm run test:unit   # astro build lalu vitest run
npm run test:e2e    # playwright test (desktop-chrome + mobile-chrome)
```

`test:unit` punya `pretest:unit` yang menjalankan `astro build` lebih dulu, karena beberapa
test membaca `dist/index.html` untuk memverifikasi redirect locale.

## Deployment

Output `dist/` adalah situs statis murni, tanpa server. Deploy ke static host mana pun
(Vercel, Cloudflare Pages, Netlify, GitHub Pages). Domain: `9drive.dev`.

## Lisensi

MIT