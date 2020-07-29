---
title: Błąd kompilatora C3482
ms.date: 11/04/2016
f1_keywords:
- C3482
helpviewer_keywords:
- C3482
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
ms.openlocfilehash: 0463f6de51e324bd02c8b766fd39909ee2803ecd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212582"
---
# <a name="compiler-error-c3482"></a>Błąd kompilatora C3482

elementu "This" można użyć tylko jako przechwytywania lambda w obrębie niestatycznej funkcji składowej

Nie można przekazać **`this`** do listy przechwytywania wyrażenia lambda, która jest zadeklarowana w metodzie statycznej lub funkcji globalnej.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Przekonwertuj otaczającą funkcję na niestatyczną metodę lub

- Usuń **`this`** wskaźnik z listy przechwytywania wyrażenia lambda.

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
