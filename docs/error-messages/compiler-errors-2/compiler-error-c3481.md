---
title: Błąd kompilatora C3481
ms.date: 11/04/2016
f1_keywords:
- C3481
helpviewer_keywords:
- C3481
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
ms.openlocfilehash: 1719e9f1d3328be083f745498e6f4ad772b0b52a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755242"
---
# <a name="compiler-error-c3481"></a>Błąd kompilatora C3481

"var": nie znaleziono zmiennej przechwytywania lambda

Kompilator nie może odnaleźć definicji zmiennej, która została przeniesiona do listy przechwytywania wyrażenia lambda.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Usuń zmienną z listy przechwytywania wyrażenia lambda.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3481, ponieważ zmienna `n` nie jest zdefiniowana:

```cpp
// C3481.cpp

int main()
{
   [n] {}(); // C3481
}
```

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)
