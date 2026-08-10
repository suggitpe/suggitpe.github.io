# Technology Stack: Pete Suggitt Personal Site (`suggitpe.github.io`)

## Core Stack
- **Static Site Generator**: Jekyll (Ruby-based static site generator)
- **Hosting & Deployment**: GitHub Pages (`https://suggitpe.github.io`)
- **Remote Theme**: `poole/hyde` (`remote_theme: poole/hyde`)
- **Markdown Renderer**: Kramdown with GitHub Flavored Markdown (`GFM`) input mode

## Plugins
- `jekyll-remote-theme`
- `jekyll-feed`
- `jekyll-seo-tag`

## Content Architecture & Collections
- **Blog Posts**: Located in `_posts/` with permalink `/blog/:year/:month/:day/:title/`
- **Presenting Collection**: Configured collection `presenting` in `_posts`/`presenting.md` with permalink `/presenting/:name/`
- **Recipes Collection**: Configured collection `recipes` in `_recipes/` with permalink `/recipes/:path/`

## Styling & Layout
- **CSS**: Vanilla CSS (`public/css/poole.css`, `public/css/hyde.css`, `public/css/syntax.css`)
- **Layout Templates**: Liquid HTML layouts (`_layouts/default.html`) and includes (`_includes/head.html`, `_includes/sidebar.html`)
