---
title: Błąd matematyczny M6111
ms.date: 11/04/2016
f1_keywords:
- M6111
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
ms.openlocfilehash: e8abedf6a326a826d0c8ac513b15037c8bf89bce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173694"
---
# <a name="math-error-m6111"></a>Błąd matematyczny M6111

Niedopełnienie stosu

Operacja zmiennoprzecinkowa spowodowała Niedopełnienie stosu na współprocesorze 8087/287/387 lub w emulatorze.

Ten błąd jest często spowodowany wywołaniem funkcji `long double`, która nie zwraca wartości. Na przykład poniższy generuje ten błąd podczas kompilowania i uruchamiania:

```
long double ld() {};
main ()
{
  ld();
}
```

Program kończy pracę z kodem zakończenia 139.
