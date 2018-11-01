---
title: STACKSIZE
ms.date: 11/04/2016
f1_keywords:
- STACKSIZE
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
ms.openlocfilehash: de2aa99375f588d682b714632590ba8e0db8ddcb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597226"
---
# <a name="stacksize"></a>STACKSIZE

Ustawia rozmiar stosu w bajtach.

```
STACKSIZE reserve[,commit]
```

## <a name="remarks"></a>Uwagi

Jest równoważne sposobem ustawienia stosu [twórz stos z alokacji](../../build/reference/stack-stack-allocations.md) (/ STACK) opcji. Zobacz dokumentację dotyczącą tej opcji, aby uzyskać szczegółowe informacje na temat *zarezerwować* i `commit` argumentów.

Ta opcja nie ma wpływu na biblioteki dll.

## <a name="see-also"></a>Zobacz też

[Zasady dla instrukcji definicji modułu](../../build/reference/rules-for-module-definition-statements.md)