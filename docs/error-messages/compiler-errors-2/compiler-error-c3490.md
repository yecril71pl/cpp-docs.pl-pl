---
title: Błąd kompilatora C3490 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3490
dev_langs:
- C++
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 503302d323f45b5f7c3971803fef0547ff28e0c8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077701"
---
# <a name="compiler-error-c3490"></a>Błąd kompilatora C3490

Nie można zmodyfikować "var", ponieważ jest on dostępny za pośrednictwem obiekt const

Wyrażenie lambda, które są zadeklarowane w `const` metody nie mogą modyfikować niemodyfikowalnej element członkowski danych.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Usuń `const` modyfikator ze swojej deklaracji metody.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3490, ponieważ modyfikuje zmienną członkowską `_i` w `const` metody:

```
// C3490a.cpp
// compile with: /c

class C
{
   void f() const
   {
      auto x = [=]() { _i = 20; }; // C3490
   }

   int _i;
};
```

## <a name="example"></a>Przykład

Poniższy przykład usuwa C3490, usuwając `const` modyfikatora w deklaracji metody:

```
// C3490b.cpp
// compile with: /c

class C
{
   void f()
   {
      auto x = [=]() { _i = 20; };
   }

   int _i;
};
```

## <a name="see-also"></a>Zobacz też

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)