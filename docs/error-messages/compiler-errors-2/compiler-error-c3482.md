---
title: Błąd kompilatora C3482
ms.date: 11/04/2016
f1_keywords:
- C3482
helpviewer_keywords:
- C3482
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
ms.openlocfilehash: 1d775551d0f4955dc4eda9b0d418ea31e065714f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743136"
---
# <a name="compiler-error-c3482"></a>Błąd kompilatora C3482

elementu "This" można użyć tylko jako przechwytywania lambda w obrębie niestatycznej funkcji składowej

Nie można przekazać `this` do listy przechwytywania wyrażenia lambda, która jest zadeklarowana w metodzie statycznej lub funkcji globalnej.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Przekonwertuj otaczającą funkcję na niestatyczną metodę lub

- Usuń wskaźnik `this` z listy przechwytywania wyrażenia lambda.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3482:

```cpp
// C3482.cpp
// compile with: /c

class C
{
public:
   static void staticMethod()
   {
      [this] {}(); // C3482
   }
};
```

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)
