---
title: Odwołania (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- objects [C++], referencing
- references [C++]
- references, to pointers
- declarations, references
- references, declaring
- referencing objects, declarator syntax
ms.assetid: 68156f7f-97a0-4b66-b26d-b25ade5e3bd8
ms.openlocfilehash: 2353f0861f0f249416d0bb84a7a951b1cb6d64bc
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857336"
---
# <a name="references-c"></a>Odwołania (C++)

Odwołanie, takie jak wskaźnik, przechowuje adres obiektu, który znajduje się w innym miejscu w pamięci. W przeciwieństwie do wskaźnika, odwołanie po jego zainicjowaniu nie może zostać wykonane w celu odwoływania się do innego obiektu lub ustawione na wartość null. Istnieją dwa rodzaje odwołań: odwołania lvalue, które odwołują się do nazwanej zmiennej i odwołania rvalue, które odwołują się do [obiektu tymczasowego](../cpp/temporary-objects.md). Operator & oznacza odwołanie lvalue, a operator & & oznacza odwołanie rvalue lub uniwersalne odwołanie (rvalue lub lvalue) w zależności od kontekstu.

Odwołania mogą być deklarowane przy użyciu następującej składni:

> \[*specyfikatory klasy magazynu*] \[*kwalifikatory CV*] *Specyfikatory typu* \[*MS-modyfikator*] *deklarator* \[ **=** *Expression*] **;**

Może zostać użyty dowolny prawidłowy deklarator określający odwołanie. O ile odwołanie nie jest odwołaniem do typu funkcji lub tablicy, stosowana jest następująca uproszczona Składnia:

> \[*specyfikatory klasy magazynu*] \[*kwalifikatory CV*] *Specyfikatory typu* \[ **&** lub **&&** ] \[*kwalifikatory CV*] *Identyfikator* \[ **=** *wyrażenie*] **;**

Odwołania są deklarowane przy użyciu następującej sekwencji:

1. Specyfikatory deklaracji:

   - Opcjonalna specyfikator urządzenia klasy magazynowania.

   - Opcjonalne kwalifikatory **const** i/lub **volatile** .

   - Specyfikator typu: nazwa typu.

1. Specyfikator:

   - Opcjonalny modyfikator właściwy dla Microsoft. Aby uzyskać więcej informacji, zobacz [Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md).

   - Operator **&** lub operator **&&** .

   - Opcjonalna **stała** i/lub **volatile** kwalifikatorów.

   - Identyfikator.

1. Opcjonalny inicjator.

Bardziej złożone formularze deklarator dla wskaźników do tablic i funkcji stosują się również do odwołań do tablic i funkcji. Aby uzyskać więcej informacji, zobacz [wskaźniki](../cpp/pointers-cpp.md).

Wiele Deklaratory i inicjatorów mogą znajdować się na liście rozdzielanej przecinkami po pojedynczym specyfikatorze deklaracji. Na przykład:

```cpp
int &i;
int &i, &j;
```

Odwołania, wskaźniki i obiekty mogą być deklarowane razem:

```cpp
int &ref, *ptr, k;
```

Odwołanie zawiera adres obiektu, ale zachowuje składnię jako obiekt.

W poniższym programie należy zauważyć, że nazwa obiektu, `s`i odwołania do obiektu `SRef`, może być używana identycznie w programach:

## <a name="example"></a>Przykład

```cpp
// references.cpp
#include <stdio.h>
struct S {
   short i;
};

int main() {
   S  s;   // Declare the object.
   S& SRef = s;   // Declare the reference.
   s.i = 3;

   printf_s("%d\n", s.i);
   printf_s("%d\n", SRef.i);

   SRef.i = 4;
   printf_s("%d\n", s.i);
   printf_s("%d\n", SRef.i);
}
```

```Output
3
3
4
4
```

## <a name="see-also"></a>Zobacz także

[Argumenty funkcji będące odwołaniami](../cpp/reference-type-function-arguments.md)<br/>
[Wartości zwracane przez funkcje będące odwołaniami](../cpp/reference-type-function-returns.md)<br/>
[Odwołania do wskaźników](../cpp/references-to-pointers.md)
