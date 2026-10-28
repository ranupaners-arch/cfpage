# cfpage

Blog pribadi berbasis Astro yang dideploy sebagai static site di Cloudflare Workers. Ditujukan untuk menulis dan membagikan artikel/catatan pribadi.

## Fitur Utama

- Daftar dan halaman detail artikel blog (Markdown & MDX) di `src/content/blog`
- Halaman "About"
- RSS feed (`/rss.xml`)
- Sitemap otomatis
- SEO dasar: canonical URL & OpenGraph meta (lihat `src/components/BaseHead.astro`)
- Observability logging bawaan Cloudflare Workers

## Tech Stack

- [Astro](https://astro.build) 5
- `@astrojs/cloudflare` — adapter deploy ke Cloudflare Workers
- `@astrojs/mdx` — dukungan MDX
- `@astrojs/sitemap` — generate sitemap
- `@astrojs/rss` — generate RSS feed
- TypeScript
- Wrangler (CLI Cloudflare) untuk dev/deploy

## Cara Menjalankan Lokal

Prasyarat: Node.js >= 22.

```bash
# install dependency
npm install

# jalankan dev server (http://localhost:4321)
npm run dev

# build untuk produksi
npm run build

# preview hasil build secara lokal (lewat wrangler)
npm run preview
```

Project ini tidak memerlukan file `.env` — konfigurasi deploy (binding assets, compatibility date, dll.) diatur lewat `wrangler.json`.

## Struktur Folder

```
src/
  components/   # komponen Astro (Header, Footer, BaseHead, dll.)
  content/
    blog/       # konten artikel (.md / .mdx)
  layouts/      # layout halaman (BlogPost.astro)
  pages/        # routing: index, about, blog/, rss.xml
  styles/       # global.css
  consts.ts     # judul & deskripsi situs
public/         # aset statis (gambar, font, favicon)
```

## Deploy

Deploy dilakukan ke Cloudflare Workers menggunakan Wrangler:

```bash
npm run build
npm run deploy
```

Tidak ada workflow CI/CD otomatis di repo ini — deploy dijalankan manual via perintah di atas.

## Kredit

Dibuat oleh **Ranupane Rimba Argana**, founder [Kukerjain](https://kukerjain.dev).

- https://kukerjain.dev
- https://ranupane.kukerjain.dev
