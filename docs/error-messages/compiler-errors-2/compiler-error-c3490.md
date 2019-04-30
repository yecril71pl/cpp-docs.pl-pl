---
title: Compiler Error C3490
ms.date: 11/04/2016
f1_keywords:
- C3490
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
ms.openlocfilehash: 1e6c3c502290e88feec89877de7ad791084401cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62381075"
---
# <a name="compiler-error-c3490"></a>Compiler Error C3490

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

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)