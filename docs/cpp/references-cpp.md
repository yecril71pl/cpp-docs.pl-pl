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
ms.openlocfilehash: 8a771b8bfc067966c3c054700538ebf180a5eb23
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233616"
---
# <a name="references-c"></a>Odwołania (C++)

Odwołanie, takie jak wskaźnik, przechowuje adres obiektu, który znajduje się w innym miejscu w pamięci. W przeciwieństwie do wskaźnika, odwołanie po jego zainicjowaniu nie może zostać wykonane w celu odwoływania się do innego obiektu lub ustawione na wartość null. Istnieją dwa rodzaje odwołań: odwołania lvalue, które odwołują się do nazwanej zmiennej i odwołania rvalue, które odwołują się do [obiektu tymczasowego](../cpp/temporary-objects.md). Operator & oznacza odwołanie lvalue, a operator && oznacza odwołanie rvalue lub uniwersalne odwołanie (rvalue lub lvalue) w zależności od kontekstu.

Odwołania mogą być deklarowane przy użyciu następującej składni:

> \[*specyfikatory klasy magazynu*] \[ *kwalifikatory CV*] *Specyfikatory typu* \[ *MS-modyfikator*] *deklarator* \[ **=** *expression*]**;**

Może zostać użyty dowolny prawidłowy deklarator określający odwołanie. O ile odwołanie nie jest odwołaniem do typu funkcji lub tablicy, stosowana jest następująca uproszczona Składnia:

> \[*specyfikatory klasy magazynu*] \[ *kwalifikatory CV*] *Specyfikatory typu* \[ **&** lub] $ **&&** \[ *-kwalifikatory* *identyfikatora* \[ **=** *expression*]**;**

Odwołania są deklarowane przy użyciu następującej sekwencji:

1. Specyfikatory deklaracji:

   - Opcjonalny specyfikator klasy magazynu.

   - Opcjonalne **`const`** i/lub **`volatile`** kwalifikatory.

   - Specyfikator typu: nazwa typu.

1. Deklarator:

   - Opcjonalny modyfikator specyficzny dla firmy Microsoft. Aby uzyskać więcej informacji, zobacz [Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md).

   - **&** Operator lub **&&** operator.

   - Opcjonalne **`const`** i/lub **`volatile`** kwalifikatorów.

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

W poniższym programie należy zauważyć, że nazwa obiektu, `s` i odwołanie do obiektu, `SRef` może być używane identycznie w programach:

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

[Argumenty funkcji typu odwołania](../cpp/reference-type-function-arguments.md)<br/>
[Funkcja typu odwołania zwraca](../cpp/reference-type-function-returns.md)<br/>
[Odwołania do wskaźników](../cpp/references-to-pointers.md)
