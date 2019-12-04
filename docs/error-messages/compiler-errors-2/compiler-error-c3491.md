---
title: Błąd kompilatora C3491
ms.date: 11/04/2016
f1_keywords:
- C3491
helpviewer_keywords:
- C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
ms.openlocfilehash: 78f90ee1c44a0d42e529a027b1e7fc90a0da3cdb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738326"
---
# <a name="compiler-error-c3491"></a>Błąd kompilatora C3491

"var": nie można zmodyfikować przechwycenia przez wartość w niemodyfikowalnym wyrażeniu lambda

Niemodyfikowalne wyrażenie lambda nie może zmodyfikować wartości zmiennej, która jest przechwytywana przez wartość.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Zadeklaruj wyrażenie lambda za pomocą słowa kluczowego `mutable` lub

- Przekaż zmienną przez odwołanie do listy przechwytywania wyrażenia lambda.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3491, ponieważ treść niemodyfikowalnego wyrażenia lambda modyfikuje zmienną przechwytywania `m`:

```cpp
// C3491a.cpp

int main()
{
   int m = 55;
   [m](int n) { m = n; }(99); // C3491
}
```

## <a name="example"></a>Przykład

Poniższy przykład rozwiązuje C3491 przez zadeklarowanie wyrażenia lambda za pomocą słowa kluczowego `mutable`:

```cpp
// C3491b.cpp

int main()
{
   int m = 55;
   [m](int n) mutable { m = n; }(99);
}
```

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)
