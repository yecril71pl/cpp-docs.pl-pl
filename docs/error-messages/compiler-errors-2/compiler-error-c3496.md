---
title: Błąd kompilatora C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: 993d391f28a59afc8926748f2e6f34ab441657dc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228859"
---
# <a name="compiler-error-c3496"></a>Błąd kompilatora C3496

element "This" jest zawsze przechwytywany przez wartość: zignorowano element "&"

Nie można przechwycić **`this`** wskaźnika przez odwołanie.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Przechwyć **`this`** wskaźnik przez wartość.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3496, ponieważ odwołanie do **`this`** wskaźnika pojawia się na liście przechwytywania wyrażenia lambda:

```cpp
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
