# DESIGN.md — 9Drive Landing Page

> Token warna dan tipografi landing page ini mengikuti design system produk 9Drive
> (Google Drive Material Design 3 clone) yang didefinisikan di
> [9drive/DESIGN.md](https://github.com/namasaiaicat/9drive-drived/blob/main/DESIGN.md).
>
> **Dokumen kanonik ada di repo `9drive`.** File ini hanya pointer supaya Stylesheet di
> `src/styles/*.css` yang meng-comment "Adhering to DESIGN.md" tetap punya rujukan lokal.

## Ringkas

Landing page memakai palet Google Drive Material Design 3 yang sama dengan aplikasi, dengan
penyesuaian berikut:

- `src/styles/theme.css` memegang token warna light/dark scheme, di-inject sebelum paint
  oleh `src/scripts/theme-init.inline.js` untuk mencegah flash.
- Section memakai warna netral sebagai latar; aksen warna hanya pada CTA dan link.
- `src/styles/navigation.css` menangani sticky navbar dan mobile drawer.

## Sumber

| Dokumen | Lokasi |
|---|---|
| Design system produk | `9drive/DESIGN.md` |
| Spec landing page | `.sokudo/specs/landing-page/design.md` (di luar repo git) |
| Aturan UI, copy, a11y, layout | `.agents/skills/antislop-*/SKILL.md` di repo `9drive` |