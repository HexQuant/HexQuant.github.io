---
layout: post
title:  "Записки моей установки Gentoo Linux"
author: HexQuant
tag: Gentoo Linux
---
[Базовая инструкция](https://packaging.python.org/en/latest/tutorials/packaging-projects/)

## Подготовка
В распорежении имеем следующие комплектующие:
* Ryzen 9 5959x
* Gigabyte B550 Aorus Pro v2
* SSD 1Tb Samsung 980 Pro NVMe M.2
* Nvidia Geforce 970 gtx

Создадим загрузочную флешку [Minimal Installation CD](https://www.gentoo.org/downloads/)
```bash
dd if=install-amd64-minimal-20220529T170531Z.iso of=/dev/sdd status=progress
```
sdd - это наша флешка. Обратите внимание что нужно указывать сам девайс, а не раздел sdd1. В случае необхоимости можно удалить существующие разделы программой sys-block/gparted

## Установка базовой системы
Схема разделов на SSD:
* sdc1 — 512M — boot
* sdc2 — 128GB — swap
* sdc3 — оставлшееся — root

/home будет смонтирован на другой диск
```bash

```
