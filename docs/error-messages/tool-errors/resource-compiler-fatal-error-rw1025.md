---
title: Błąd krytyczny kompilatora zasobów RW1025 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW1025
dev_langs:
- C++
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2bf7bdeed320c004ffb75fa1d25d9b89147b0c13
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117403"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>Błąd krytyczny kompilatora zasobów RW1025

Za mało pamięci sterty daleko

Sprawdź, czy oprogramowanie rezydentnego może trwać zbyt dużej ilości miejsca. Aby dowiedzieć się, jak ilość pamięci, masz, należy użyć programu CHKDSK.

Jeśli tworzysz duży plik zasobów, należy podzielić na dwa pliki skryptów zasobów. Po utworzeniu dwa pliki .res, należy użyć wiersza polecenia systemu MS-DOS do dołączenia do nich razem:

```
copy first.res /b + second.res /b full.res
```