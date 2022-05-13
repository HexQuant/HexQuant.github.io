---
layout: post
title:  "Дебагинг модулей Python на С в vscode"
author: HexQuant
tag: Python C Extensions
---

1. Установите расширение [Python C++ Debugger](https://marketplace.visualstudio.com/items?itemName=benjamin-simmonds.pythoncpp-debug)
2. Создайте файл "launch.json":
```
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Python C++ Debugger",
            "type": "pythoncpp",
            "request": "launch",
            "pythonConfig": "default",
            "cppConfig": "default (gdb) Attach"
        }
    ]
}
```
3. Не забудте собрать дебаг версию модуля
```bash
python setup.py clean --all && python setup.py build --debug install
```
4. Убедитесь, что ptrace_scope выставлен в 0 или отладчику даны права рута
```bash
echo 0 | sudo tee /proc/sys/kernel/yama/ptrace_scope
```
5. Готово, можно ставить бряки и отлаживать
