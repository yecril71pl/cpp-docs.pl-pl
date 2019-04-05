---
title: Compiler Error C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: 025498f3fe244916cd0a06e36feee6fdb532acc6
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59026702"
---
# <a name="compiler-error-c3496"></a>Compiler Error C3496

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

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)