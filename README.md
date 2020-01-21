# Блога Cronbox

## Как добавить новый пост

Создаем в каталоге content новый файл с расширением `.md`.

В файле добавляем шапку (frontmatter) вида:

```toml
+++
title = "Генератор статических сайтов Zola"
date = 2020-01-01

[taxonomies]
tags = ["zola"]
categories = ["tutorial"]
+++
```

В списках `tags` и `categories` задаем тэги и категории.