---
title: Błąd kompilatora C3485
ms.date: 11/04/2016
f1_keywords:
- C3485
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
ms.openlocfilehash: 0eacb6ce6426674d23fc78596ead3730f46ae370
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743045"
---
# <a name="compiler-error-c3485"></a>Błąd kompilatora C3485

Definicja lambda nie może mieć żadnych kwalifikatorów CV

Nie można użyć kwalifikatora `const` ani `volatile` jako części definicji wyrażenia lambda.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Usuń kwalifikator `const` lub `volatile` z definicji wyrażenia lambda.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3485, ponieważ używa kwalifikatora `const` jako części definicji wyrażenia lambda:

```cpp
// C3485.cpp

int main()
{
   auto x = []() const mutable {}; // C3485
}
```

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)
