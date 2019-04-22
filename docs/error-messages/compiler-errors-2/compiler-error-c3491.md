---
title: Błąd kompilatora C3491
ms.date: 11/04/2016
f1_keywords:
- C3491
helpviewer_keywords:
- C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
ms.openlocfilehash: 12f50e48fc18fc23d078b6dbc7d21d05efa06d43
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032930"
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

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)