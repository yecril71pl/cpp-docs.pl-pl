---
title: Błąd kompilatora C3490
ms.date: 11/04/2016
f1_keywords:
- C3490
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
ms.openlocfilehash: ea7341b9c587a764c7366fa7b7c89e4fc67bc7d8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230860"
---
# <a name="compiler-error-c3490"></a>Błąd kompilatora C3490

nie można zmodyfikować elementu "var", ponieważ jest on dostępny za pomocą obiektu const

Wyrażenie lambda zadeklarowane w **`const`** metodzie nie może modyfikować niemodyfikowalnych danych elementu członkowskiego.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Usuń **`const`** modyfikator z deklaracji metody.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3490, ponieważ modyfikuje zmienną członkowską `_i` w **`const`** metodzie:

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

Poniższy przykład rozwiązuje C3490 przez usunięcie **`const`** modyfikatora z deklaracji metody:

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
