---
title: STACKSIZE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- STACKSIZE
dev_langs:
- C++
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7d9b61febedde1a2647df6312a8588b08c6bdad7
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705565"
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