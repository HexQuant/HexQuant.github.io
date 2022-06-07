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
* 32x2 GB RAM
* SSD 1Tb Samsung 980 Pro NVMe M.2
* 2 TB HDD
* Nvidia Geforce 970 gtx

Создадим загрузочную флешку [Minimal Installation CD](https://www.gentoo.org/downloads/)
```bash
dd if=install-amd64-minimal-20220529T170531Z.iso of=/dev/sdd status=progress
```
sdd - это наша флешка. Обратите внимание что нужно указывать сам девайс, а не раздел sdd1. В случае необхоимости можно удалить существующие разделы программой sys-block/gparted

## Установка базовой системы

Схема разделов на SSD:
| Раздел         | Размер    | Цель      | Файловая система |
|----------------|-----------|-----------|------------------|
| /dev/nmve0n1p1 | 512M      | /boot/efi | fat32            |
| /dev/nmve0n1p2 | 512M      | /boot     | ext2             |
| /dev/nmve0n1p3 | 64GB      | swap      | none             |
| /dev/nmve0n1p4 | остальное | /         | ext4             |

/home будет смонтирован на другой диск

Разметрку делаем при помощи fdisk или более дружелюбном его аналоге Cfdisk.
```bash

```
