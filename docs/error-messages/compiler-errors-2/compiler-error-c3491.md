---
title: Błąd kompilatora C3491 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3491
dev_langs:
- C++
helpviewer_keywords:
- C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 64d7b2e4bd602a53afeba2f77293c31bb28902d3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068770"
---
# <a name="compiler-error-c3491"></a>Błąd kompilatora C3491

"var": nie można zmodyfikować przechwytywania przez wartość w niemodyfikowalnym wyrażeniu lambda

Wyrażenie niemodyfikowalnym wyrażeniu lambda nie można zmodyfikować wartość zmiennej, która jest przechwytywana przez wartość.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Zadeklaruj Wyrażenie lambda z `mutable` — słowo kluczowe, lub

- Przekazanie zmiennej w odniesieniu do listy przechwytywania wyrażenia lambda.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3491, ponieważ treść wyrażenia niemodyfikowalnym wyrażeniu lambda modyfikuje zmienną przechwytywania `m`:

```
// C3491a.cpp

int main()
{
   int m = 55;
   [m](int n) { m = n; }(99); // C3491
}
```

## <a name="example"></a>Przykład

Poniższy przykład usuwa C3491 przez zadeklarowanie wyrażenia lambda z `mutable` — słowo kluczowe:

```
// C3491b.cpp

int main()
{
   int m = 55;
   [m](int n) mutable { m = n; }(99);
}
```

## <a name="see-also"></a>Zobacz też

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)