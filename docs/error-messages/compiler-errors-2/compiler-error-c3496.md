---
title: Błąd kompilatora C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: b9542f1904c6797a77c88c88a37aff9348364268
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738183"
---
# <a name="compiler-error-c3496"></a>Błąd kompilatora C3496

element "This" jest zawsze przechwytywany przez wartość: zignorowano element "&"

Nie można przechwycić `this` wskaźnika przez odwołanie.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Przechwyć `this` wskaźnik według wartości.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3496, ponieważ odwołanie do wskaźnika `this` pojawia się na liście przechwytywania wyrażenia lambda:

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
