---
# Post de ejemplo, de referencia. Está en _drafts/, así que no se publica.
# Para un post nuevo: copiarlo a _posts/AAAA-MM-DD-titulo.md y editarlo.
# Para verlo en el preview: bundle exec jekyll serve --drafts
layout: post                 # siempre "post"
title: Ejemplo de post       # aparece en /blog/ y como título de la página
date: 2025-10-10             # ordena el post; el año va en la URL (/blog/2025/...)
description: Una línea que aparece debajo del título en la lista del blog.
tags: [ejemplo, categorías]  # opcional; cada tag tiene su página /blog/tag/<tag>/
news: true                   # opcional; si está, el post aparece también en News
# related_posts: false       # opcional; descomentar para ocultar "related posts" al final
---

Este primer párrafo es el extracto: es lo que se ve en la lista de noticias, seguido de "Read more →" (solo si `news: true`).

A partir de acá, el resto del post solo se ve en la página completa. Se escribe en Markdown normal: _itálica_, **negrita**, [links](https://gabrielgorenroig.github.io), listas:

- un ítem
- otro ítem

Y también matemática con MathJax, en línea como $f \dashv g$ o en display:

$$
\mathrm{Hom}(F A, B) \cong \mathrm{Hom}(A, G B)
$$
