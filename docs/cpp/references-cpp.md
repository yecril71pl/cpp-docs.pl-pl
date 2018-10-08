---
title: Odwołania (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- objects [C++], referencing
- references [C++]
- references, to pointers
- declarations, references
- references, declaring
- referencing objects, declarator syntax
ms.assetid: 68156f7f-97a0-4b66-b26d-b25ade5e3bd8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a3a93d434907a2a3ff13053ee4b932201de22f3a
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861411"
---
# <a name="references-c"></a>Odwołania (C++)

Odwołania, jak wskaźnik, przechowuje adres obiektu, który znajduje się w innym miejscu w pamięci. W przeciwieństwie do wskaźnika, odwołania po jego zainicjowaniu nie można wprowadzać odnoszą się do innego obiektu lub ustawiona na wartość null. Istnieją dwa rodzaje odwołań: odwołania lvalue, które odnoszą się do nazwanej odwołania zmiennej i r-wartości, które odnoszą się do [tymczasowy obiekt](../cpp/temporary-objects.md). & — Operator oznacza odwołanie lvalue i & & — operator oznacza odwołanie rvalue lub odwołaniem universal (rvalue lub l-wartości) w zależności od kontekstu.

Odwołania może być zadeklarowana przy użyciu następującej składni:

> \[*Specyfikatory klas magazynu*] \[ *kwalifikatory cv*] *specyfikatory typu* \[ *modyfikator ms*]  *deklarator* \[ **=** *wyrażenie*]**;**

Wszystkie prawidłowe deklaratora, określając odwołanie mogą być używane. Chyba, że odwołanie jest odwołanie do typu funkcji lub tablicy, mają zastosowanie następujące uproszczoną składnię:

> \[*Specyfikatory klas magazynu*] \[ *kwalifikatory cv*] *specyfikatory typu* \[ **&** lub **&&**] \[ *kwalifikatory cv*] *identyfikator* \[ **=** *wyrażenie*]**;**

Odwołania są zadeklarowane za pomocą następującej sekwencji:

1. Specyfikatory deklaracji:

   - Specyfikator klasy magazynowania opcjonalne.

   - Opcjonalnie **const** i/lub **volatile** kwalifikatorów.

   - Specyfikator typu: Nazwa typu.

1. Specyfikator:

   - Opcjonalny modyfikator właściwy dla Microsoft. Aby uzyskać więcej informacji, zobacz [Modyfikatory specyficzne dla Microsoft](../cpp/microsoft-specific-modifiers.md).

   - **&** Operatora lub **&&** operatora.

   - Opcjonalnie **const** i/lub **volatile** qualifers.

   - Identyfikator.

1. Opcjonalny inicjator.

Formularze deklaratorów bardziej złożonych wskaźniki do tablic i funkcji mają zastosowanie również do odwołań do tablic i funkcji. Aby uzyskać więcej informacji, zobacz [wskaźniki](../cpp/pointers-cpp.md).

Wiele deklaratorów i inicjatory mogą występować w rozdzielana przecinkami lista specyfikator jednej deklaracji. Na przykład:

```cpp
int &i;
int &i, &j;
```

Odwołania, wskaźniki i obiekty mogą być zadeklarowane jednocześnie:

```cpp
int &ref, *ptr, k;
```

Odwołanie przechowuje adres obiektu, ale składniowo zachowuje się jak obiekt.

W następujący program, zwróć uwagę, że nazwa obiektu, `s`i odwołania do obiektu, `SRef`, mogą być używane tak samo w programach:

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
