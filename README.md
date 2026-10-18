# Manga Downloader Plus: the search catalogs

One file per site under `catalog/`: every series the site lists (title, link,
other names, and for some sites the latest chapter number), gzipped, plus
`index.json` (each file's size and checksum, when it was made) and
`sources.json` (the Tachiyomi sources the plugin crawl used). The app and the
CLI download from here, through `raw.githubusercontent.com`, only the files
whose checksum changed; see `catalog.BaseURL` in the code.

The files are rebuilt here, by this repository's own workflows, with the
crawlers of [Xopper/manga-downloader](https://github.com/Xopper/manga-downloader)
(private):

- `catalog.yaml`: our own crawlers. The fast families every night, every
  family on Sunday.
- `catalog-suwayomi.yaml`: the Tachiyomi plugins, on Sunday, only for the
  sites our crawlers can't list.

Both check the code out with the `CODE_SSH_KEY` secret: the private half of
a deploy key registered read-only on `Xopper/manga-downloader` (its Settings
→ Deploy keys), set in this repository's Settings → Secrets and variables →
Actions. Without it the workflows fail at their second step.

This repository is public so that the app can read it without a login and so
that the workflows run on GitHub's free minutes for public repositories. It
holds data only, no code.
