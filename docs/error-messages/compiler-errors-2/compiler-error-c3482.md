---
title: Błąd kompilatora C3482
ms.date: 11/04/2016
f1_keywords:
- C3482
helpviewer_keywords:
- C3482
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
ms.openlocfilehash: ec0018fc1aafc7e3e0423608f4db9f78946e4597
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432646"
---
# <a name="compiler-error-c3482"></a>Błąd kompilatora C3482

"this" należy używać tylko jako przechwyt lambdy w obrębie funkcji niestatycznego elementu członkowskiego

Nie można przekazać `this` do listy przechwytywania wyrażenia lambda, które są zadeklarowane w statycznej metody lub funkcją globalną.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Konwertuj funkcji otaczającej metody niestatyczna, lub

- Usuń `this` wskaźnika z listy przechwytywania wyrażenia lambda.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3482:

```
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

## <a name="see-also"></a>Zobacz też

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)