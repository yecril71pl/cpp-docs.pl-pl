---
title: Błąd kompilatora C3485
ms.date: 11/04/2016
f1_keywords:
- C3485
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
ms.openlocfilehash: 2fcaecd6be35e2ae6822133930b48b6bbf02aafe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62381146"
---
# <a name="compiler-error-c3485"></a>Błąd kompilatora C3485

Definicja lambdy nie może mieć żadnych kwalifikatorów cv

Nie można użyć `const` lub `volatile` kwalifikator jako część definicji wyrażenia lambda.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Usuń `const` lub `volatile` kwalifikator z definicji w wyrażeniu lambda.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3485, ponieważ używa ona `const` kwalifikator jako część definicji wyrażenia lambda:

```
// C3485.cpp

int main()
{
   auto x = []() const mutable {}; // C3485
}
```

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)