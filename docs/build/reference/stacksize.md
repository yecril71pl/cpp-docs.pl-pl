---
title: STACKSIZE
ms.date: 11/04/2016
f1_keywords:
- STACKSIZE
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
ms.openlocfilehash: 2d27b4fd596098f4abc5bb0d804d87bd08f70a60
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318359"
---
# <a name="stacksize"></a>STACKSIZE

Ustawia rozmiar stosu w bajtach.

```
STACKSIZE reserve[,commit]
```

## <a name="remarks"></a>Uwagi

Jest równoważne sposobem ustawienia stosu [twórz stos z alokacji](stack-stack-allocations.md) (/ STACK) opcji. Zobacz dokumentację dotyczącą tej opcji, aby uzyskać szczegółowe informacje na temat *zarezerwować* i `commit` argumentów.

Ta opcja nie ma wpływu na biblioteki dll.

## <a name="see-also"></a>Zobacz także

[Zasady dla instrukcji definicji modułu](rules-for-module-definition-statements.md)
