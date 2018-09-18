---
title: Błąd kompilatora C2513 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2513
dev_langs:
- C++
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82df537e49ca17140d70977486314f43a072022d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045435"
---
# <a name="compiler-error-c2513"></a>Błąd kompilatora C2513

"type": Brak deklaracji zmiennej przed "="

Specyfikator typu pojawia się w deklaracji z nie zmiennej identyfikatora.

Poniższy przykład spowoduje wygenerowanie C2513:

```
// C2513.cpp
int main() {
   int = 9;   // C2513
   int i = 9;   // OK
}
```

Ten błąd może być też wygenerowany w wyniku pracy zgodność kompilatora Visual Studio .NET 2003: inicjowanie typedef nie są już dozwolone. Inicjowanie typedef nie jest dozwolona przez standardowe i generuje błąd kompilatora.

```
// C2513b.cpp
// compile with: /c
typedef struct S {
   int m_i;
} S = { 1 };   // C2513
// try the following line instead
// } S;
```

Alternatywą jest nieusuwanie `typedef` do definiujemy zmienną z listy inicjatorów agregacji, ale nie jest zalecane, ponieważ spowoduje to utworzenie zmiennej o nazwie identycznej z nazwą typu i ukryć nazwę typu.