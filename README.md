# Página do grupo BDRI (UFAM)

Site estático em Jekyll, compatível com GitHub Pages. O conteúdo fica em arquivos de dados:

- `_data/people.yml`: líderes, membros e egressos. Membros só aparecem com `public: yes`.
- `_data/publications.yml`: publicações (hoje, as de Altigran desde 2021, extraídas do DBLP).
- `index.md`, `projetos/`, `contato/`: texto das páginas.

## Preview local

```
docker run --rm -p 4000:4000 -v "$PWD":/srv/jekyll -w /srv/jekyll ruby:3.3 \
  bash -c "bundle install && bundle exec jekyll serve --host 0.0.0.0 --config _config.yml,_config_preview.yml"
```

`_config_preview.yml` liga `show_pending`, que mostra também os membros ainda não confirmados (com o selo "a confirmar").

## Publicar

Ver `PENDING.md` antes. Em GitHub Pages: Settings → Pages → branch `main`, pasta `/ (root)`. Depois preencher `url` em `_config.yml`.
