---
title: Błąd kompilatora C3490
ms.date: 11/04/2016
f1_keywords:
- C3490
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
ms.openlocfilehash: 940eae39222548ec74bda8ccb38e669748ffa74f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738404"
---
# <a name="compiler-error-c3490"></a>Błąd kompilatora C3490

nie można zmodyfikować elementu "var", ponieważ jest on dostępny za pomocą obiektu const

Wyrażenie lambda zadeklarowane w metodzie `const` nie może modyfikować niemodyfikowalnych danych elementu członkowskiego.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Usuń modyfikator `const` z deklaracji metody.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3490, ponieważ modyfikuje zmienną członkowską `_i` w metodzie `const`:

```cpp
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

Poniższy przykład rozwiązuje C3490 przez usunięcie modyfikatora `const` z deklaracji metody:

```cpp
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
