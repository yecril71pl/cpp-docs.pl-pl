---
title: Błąd krytyczny kompilatora zasobów RW1025
ms.date: 11/04/2016
f1_keywords:
- RW1025
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
ms.openlocfilehash: 8ecfc11f5cc991294d966a4b6c75d8da6669d5b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575685"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>Błąd krytyczny kompilatora zasobów RW1025

Za mało pamięci sterty daleko

Sprawdź, czy oprogramowanie rezydentnego może trwać zbyt dużej ilości miejsca. Aby dowiedzieć się, jak ilość pamięci, masz, należy użyć programu CHKDSK.

Jeśli tworzysz duży plik zasobów, należy podzielić na dwa pliki skryptów zasobów. Po utworzeniu dwa pliki .res, należy użyć wiersza polecenia systemu MS-DOS do dołączenia do nich razem:

```
copy first.res /b + second.res /b full.res
```