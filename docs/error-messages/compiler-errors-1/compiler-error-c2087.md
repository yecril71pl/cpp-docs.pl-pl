---
title: Błąd kompilatora C2087 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2087
dev_langs:
- C++
helpviewer_keywords:
- C2087
ms.assetid: 89761e83-415a-4468-a4c6-b6dedfd1dd6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38b6ce6c0b2435143ece8d431271c97a3f48a2b2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101959"
---
# <a name="compiler-error-c2087"></a>Błąd kompilatora C2087

'Identyfikator': Brak indeksu dolnego

Definicja tablicy o liczbie wiele indeksów dolnych Brak indeksu dolnego wartości wyższej niż jeden wymiar.

Poniższy przykład spowoduje wygenerowanie C2087:

```
// C2087.cpp
int main() {
   char a[10][];   // C2087
}
```

Możliwe rozwiązanie:

```
// C2087b.cpp
int main() {
   char b[4][5];
}
```