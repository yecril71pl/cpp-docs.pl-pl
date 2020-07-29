---
title: Błąd kompilatora C3485
ms.date: 11/04/2016
f1_keywords:
- C3485
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
ms.openlocfilehash: 2117832ffd5a90612e9745a3706f01e3b5d1b18d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87197673"
---
# <a name="compiler-error-c3485"></a>Błąd kompilatora C3485

Definicja lambda nie może mieć żadnych kwalifikatorów CV

Nie można użyć **`const`** **`volatile`** kwalifikatora lub jako części definicji wyrażenia lambda.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Usuń **`const`** kwalifikator lub **`volatile`** z definicji wyrażenia lambda.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3485, ponieważ używa **`const`** kwalifikatora jako części definicji wyrażenia lambda:

```cpp
// C3485.cpp

int main()
{
   auto x = []() const mutable {}; // C3485
}
```

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)
