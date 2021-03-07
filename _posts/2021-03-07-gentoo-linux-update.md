---
layout: post
title:  "Welcome to Jekyll!"
---

# Обновление пакетов Gentoo Linux
```console
emerge --ask --update --deep --newuse --verbose-conflicts --with-bdeps=y @world
```
## Проблемы при обновлении пакетов
### Конфликт слотов
Проверить где используется наш пакет, например dev-lang/ghc:

```console
qdepends -Q '%{CAT}/%{PN}:%{SLOT}' ^dev-lang/ghc
```

Принудительно провести пересборку всех кто зависит от dev-lang/ghc:

```console
emerge --ignore-default-opts -va1 --keep-going $( qdepends -CQqqF '%{CAT}/%{PN}:%{SLOT}' '^dev-lang/ghc' )
```
