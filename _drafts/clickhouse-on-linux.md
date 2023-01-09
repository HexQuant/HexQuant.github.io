---
layout: post
title: "Установка и запуск ClickHouse на Gentoo"
author: HexQuant
tags: ClickHouse Linux
---

## Установка
### Пишем свой Ebuild
[Официальная иструкция по сборке ClickHouse под Linux](https://clickhouse.com/docs/en/development/build)
```bash
# Copyright 2023 Gentoo Authors
# Distributed under the terms of the GNU General Public License v2

EAPI=8

DESCRIPTION="The open-source column-oriented database management system that allows generating analytical data reports in real-time"
HOMEPAGE="https://clickhouse.com/"
SRC_URI=""
if [[ "${PV}" = *9999* ]]; then
	EGIT_REPO_URI="https://github.com/ClickHouse/ClickHouse.git"
else
	SRC_URI="https://github.com/ClickHouse/archive/v${PV}-stable.tar.gz -> ${P}.tar.gz"
	KEYWORDS="~amd64"
fi

LICENSE="Apache-2.0"
SLOT="0"

DEPEND=""
RDEPEND="${DEPEND}"
BDEPEND=""
```
Актуальный ebuild moжно взять в [моём репозитории](https://github.com/HexQuant/gentoo-overlay).
## Запуск
### Настройка удалённого доступа
### Автозагрузка ClickHouse при запуске Gentoo

[Альтернативная инструкция](https://dondub.com/2021/06/zapusk-subd-clickhouse-na-gentoo/)
