# AGENTS.md

## Project

Landing page statis untuk 9Drive. Astro 5 + React 19 islands. Tidak ada backend, database,
atau auth. Output `dist/` adalah situs statis murni.

Kode aplikasi 9Drive ada di repo terpisah: `9drive` (backend, frontend, CLI).

## Commands

- `npm run dev`: dev server di `localhost:4321`
- `npm run build`: build statis ke `dist/`
- `npm run preview`: serve hasil build
- `npm run lint`: `tsc --noEmit`
- `npm run test:unit`: unit test Vitest (`pretest:unit` menjalankan `astro build` dulu)
- `npm run test:e2e`: Playwright, proyek `desktop-chrome` dan `mobile-chrome`

## Conventions

- Halaman per locale di `src/pages/{en,id}/`. Root `index.astro` hanya redirect.
- Semua teks user-facing ada di `src/data/locales/{en,id}.ts`, ditipe lewat `Dictionary`
  di `src/types/index.ts`. Jangan hardcode string di komponen.
- Island React pakai directive `client:` (`client:load` untuk yang di atas fold,
  `client:visible` untuk yang di bawah). Komponen statis tetap `.astro`/`.tsx` tanpa
  directive.
- Token warna hanya lewat CSS custom properties di `src/styles/theme.css`. Jangan pakai
  warna hex langsung di komponen.
- Tema lewat `src/scripts/theme-init.inline.js` yang blocking sebelum paint, plus island
  `ThemeToggle` yang membaca `utils/storage.ts`. Jangan tambah sumber flash.
- Aksesibilitas: island yang interaktif wajib punya ARIA yang sesuai dan keyboard support.
  Ada E2E audit via axe-core di `e2e/accessibility.spec.ts`.

## Verification

Sebelum finish: `npm run lint` dan `npm run test:unit`. Ubah layout atau markup?
Jalankan juga `npm run test:e2e`, karena ada test routing/anchor dan theme FOIT.

## Rules

- Jangan tambah dependency tanpa alasan jelas; Astro cukup untuk situs ini.
- Jangan edit `dist/`, `.astro/`, atau `node_modules/`.
- Jangan hardcode `9drive.dev` di komponen; lewat `astro.config.mjs` atau dictionary.
- Copy harus lolos review `.agents/skills/antislop-copywriting/` di repo `9drive` untuk
  marketing/UI/text, `antislop-human/` untuk aksesibilitas.