---
title: Błąd matematyczny M6111 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6111
dev_langs:
- C++
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95a55ec6b7cdf0b6e4c15bd283dde77c610698fa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074828"
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