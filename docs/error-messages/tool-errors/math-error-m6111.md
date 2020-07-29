---
title: Błąd matematyczny M6111
ms.date: 11/04/2016
f1_keywords:
- M6111
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
ms.openlocfilehash: 986c0e53edcddfc47eb9ba970f3c32385e0a57d9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225192"
---
# <a name="math-error-m6111"></a>Błąd matematyczny M6111

Niedopełnienie stosu

Operacja zmiennoprzecinkowa spowodowała Niedopełnienie stosu na współprocesorze 8087/287/387 lub w emulatorze.

Ten błąd jest często spowodowany wywołaniem **`long double`** funkcji, która nie zwraca wartości. Na przykład poniższy generuje ten błąd podczas kompilowania i uruchamiania:

```
long double ld() {};
main ()
{
  ld();
}
```

Program kończy pracę z kodem zakończenia 139.
