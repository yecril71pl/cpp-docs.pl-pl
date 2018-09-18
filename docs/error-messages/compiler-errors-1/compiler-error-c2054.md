---
title: Błąd kompilatora C2054 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2054
dev_langs:
- C++
helpviewer_keywords:
- C2054
ms.assetid: 37f7c612-0d7d-4728-9e67-ac4160555f48
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5fc936bf6c42144a55bc6d84a8434959383e7e9f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071435"
---
# <a name="compiler-error-c2054"></a>Błąd kompilatora C2054

Oczekiwano ' (' z 'Identyfikator'

Identyfikator funkcji jest używany w kontekście, który wymaga końcowe nawiasów.

Ten błąd może być spowodowany, pomijając znak równości (=) na inicjalizację złożony.

Poniższy przykład spowoduje wygenerowanie C2054:

```
// C2054.c
int array1[] { 1, 2, 3 };   // C2054, missing =
```

Możliwe rozwiązanie:

```
// C2054b.c
int main() {
   int array2[] = { 1, 2, 3 };
}
```