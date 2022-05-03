---
layout: post
title:  "Обновление пакетов в Gentoo Linux"
author: HexQuant
tag: Gentoo Linux
---

## Обновление спустя долгое время
Для начала лучше сконцентрироваться на обновлении системного сета:

```console
emerge -avuDN @system
```

Затем можно приступать к обновлению мира:

```console
emerge -avquDNp @world
```

Если конфликтов слишком много, то стоит убрать флаги -D(считывать полное дерево зависимостей пакетов вместо проверки прямых зависимостей) и -N(включить в список на установку уже установленные пакеты, в которых с момента предыдущей компиляции изменились USE-флаги).

Так-же можно добавить **--backtrack=9999** (по умолчанию 10).

## Проблемы при обновлении пакетов
### Конфликт слотов
Проверить где используется наш пакет, например ***dev-lang/ghc***:

```console
qdepends -Q '%{CAT}/%{PN}:%{SLOT}' ^dev-lang/ghc
```

Принудительно провести пересборку всех кто зависит от ***dev-lang/ghc***:

```console
emerge --ignore-default-opts -va1 --keep-going=y $( qdepends -CQqqF '%{CAT}/%{PN}:%{SLOT}' '^dev-lang/ghc' )
```

### Блокировка
Удалить всех кто блокирует пакет ***dev-lang/ghc***
```console
emerge -C $(qlist -IC dev-lang/ghc)
```
Удалить все пакеты Qt и установить заново
```console
export INSTALLED_QT_PACKAGES=$(qlist -IC "dev-qt/*") && emerge -Ca ${INSTALLED_QT_PACKAGES} && emerge -av1 ${INSTALLED_QT_PACKAGES}
```
