---
title: Błąd kompilatora C3485 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3485
dev_langs:
- C++
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db3eee53f23aa2cdc958b63faed11ead302f4b1e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060749"
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

## <a name="see-also"></a>Zobacz też

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)