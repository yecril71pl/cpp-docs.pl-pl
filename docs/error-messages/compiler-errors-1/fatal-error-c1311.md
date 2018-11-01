---
title: Błąd krytyczny C1311
ms.date: 11/04/2016
f1_keywords:
- C1311
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
ms.openlocfilehash: ba2b797c9bf521533e7c2ccff8d358b6216d392f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637908"
---
# <a name="fatal-error-c1311"></a>Błąd krytyczny C1311

COFF format statycznie nie może zainicjować "var" przy użyciu numeru bajtem(ów) adresu

Adres, którego wartość nie jest znany w czasie kompilacji nie statycznie przypisany do zmiennej, którego typ ma magazynu mniej niż cztery bajty.

Ten błąd może wystąpić na kod, który jest prawidłowy w języku C++.

Poniższy przykład przedstawia jeden warunek, który może spowodować C1311.

```
char c = (char)"Hello, world";   // C1311
char *d = (char*)"Hello, world";   // OK
```