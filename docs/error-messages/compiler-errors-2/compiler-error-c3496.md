---
title: Błąd kompilatora C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: c0075bf0e3749966a5e5b9fcd775b5d73171bf17
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599423"
---
# <a name="compiler-error-c3496"></a>Błąd kompilatora C3496

"this" jest zawsze przechwytywany przez wartość: "&" jest ignorowany

Nie można dokonać przechwytu `this` wskaźnika przez odwołanie.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Przechwytywanie `this` wskaźnik przez wartość.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3496, ponieważ odwołanie do `this` wskaźnika, który pojawia się na liście przechwytywania wyrażenia lambda:

```
// C3496.cpp
// compile with: /c

class C
{
   void f()
   {
      [&this] {}(); // C3496
   }
};
```

## <a name="see-also"></a>Zobacz też

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)