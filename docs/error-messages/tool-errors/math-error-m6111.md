---
title: Błąd matematyczny M6111
ms.date: 11/04/2016
f1_keywords:
- M6111
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
ms.openlocfilehash: 44f406881d64d13e23ca2c0911ee278c864a2c11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393411"
---
# <a name="math-error-m6111"></a>Błąd matematyczny M6111

Niedopełnienie stosu

W wyniku operacji zmiennoprzecinkowej Niedopełnienie stosu w Koprocesor 8087/287/387 lub emulator.

Ten błąd jest często spowodowane przez wywołanie `long double` funkcja, która nie zwraca wartości. Na przykład następujące generuje ten błąd, gdy skompilowane i uruchom:

```
long double ld() {};
main ()
{
  ld();
}
```

Program kończy się z kodem zakończenia 139.