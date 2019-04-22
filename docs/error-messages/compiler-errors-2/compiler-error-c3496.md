---
title: Compiler Error C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: 025498f3fe244916cd0a06e36feee6fdb532acc6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
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