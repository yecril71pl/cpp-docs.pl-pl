---
title: Wbudowane operatory, pierwszeństwo i łączność języka C++
ms.date: 07/23/2020
helpviewer_keywords:
- operators (C++), hierarchy
- operator precedence
- precedence, operators
- operators (C++), associativity
- multiple operators [C++]
- associativity of operators [C++]
- operators [C++], precedence
- evaluation order
- hierarchy, operator
ms.assetid: 95c1f0ba-dad8-4034-b039-f79a904f112f
ms.openlocfilehash: 10c9e5db569ba211ed8d42386816b4f6bb71ee29
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221773"
---
# <a name="c-built-in-operators-precedence-and-associativity"></a>Wbudowane operatory, pierwszeństwo i łączność języka C++

Język C++ obejmuje wszystkie operatory C i dodaje kilka nowych operatorów. Operatory określają oszacowania wykonywane na jednym lub większej liczbie operandów.

## <a name="precedence-and-associativity"></a>Pierwszeństwo i łączność

*Pierwszeństwo* operatorów określa kolejność operacji w wyrażeniach, które zawierają więcej niż jeden operator. Operator *łączność* określa, czy w wyrażeniu zawierającym wiele operatorów z tym samym pierwszeństwem operand jest zgrupowany z jedną po lewej lub po prawej stronie.

## <a name="alternative-spellings"></a>Alternatywne pisownie

Język C++ określa alternatywne pisownie dla niektórych operatorów. W języku C alternatywna pisownia jest podawana jako makra w \<iso646.h> nagłówku. W języku C++ te alternatywy są słowami kluczowymi, a użycie \<iso646.h> lub odpowiednik języka C++ \<ciso646> jest przestarzałe. W programie Microsoft C++ [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) Opcja kompilatora or jest wymagana do włączenia alternatywnych pisowni.

## <a name="c-operator-precedence-and-associativity-table"></a>Nadrzędne operatory języka C++ i tabela łączność

W poniższej tabeli przedstawiono pierwszeństwo i łączność operatorów C++ (od najwyższego do najniższego pierwszeństwa). Operatory o tym samym numerze pierwszeństwa mają równe pierwszeństwo, chyba inny stosunek jest jawnie wymuszony przez nawiasy.

| Opis operatora | Operator | Różne |
|--|--|--|
| **Pierwszeństwo grupy 1, brak łączność** |
| [Rozpoznawanie zakresu](../cpp/scope-resolution-operator.md) | [`::`](../cpp/scope-resolution-operator.md) |
| **Pierwszeństwo grupy 2, od lewej do prawej łączność** |
| [Wybór elementu członkowskiego (obiekt lub wskaźnik)](../cpp/member-access-operators-dot-and.md) | [`.`oraz`->`](../cpp/member-access-operators-dot-and.md) |
| [Indeks dolny tablicy](../cpp/subscript-operator.md) | [`[]`](../cpp/subscript-operator.md) |
| [Wywołanie funkcji](../cpp/function-call-operator-parens.md) | [`()`](../cpp/function-call-operator-parens.md) |
| [Przyrost Przyrostkowy](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md) | [`++`](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md) |
| [Zmniejszenie przyrostu](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md) | [`--`](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md) |
| [Nazwa typu](../cpp/typeid-operator.md) | [`typeid`](../cpp/typeid-operator.md) |
| [Konwersja typu stałego](../cpp/const-cast-operator.md) | [`const_cast`](../cpp/const-cast-operator.md) |
| [Konwersja typu dynamicznego](../cpp/dynamic-cast-operator.md) | [`dynamic_cast`](../cpp/dynamic-cast-operator.md) |
| [Konwersja typu reinterpretowanego](../cpp/reinterpret-cast-operator.md) | [`reinterpret_cast`](../cpp/reinterpret-cast-operator.md) |
| [Konwersja typu statycznego](../cpp/static-cast-operator.md) | [`static_cast`](../cpp/static-cast-operator.md) |
| **Pierwszeństwo grupy 3, od prawej do lewej łączność** |
| [Rozmiar obiektu lub typu](../cpp/sizeof-operator.md) | [`sizeof`](../cpp/sizeof-operator.md) |
| [Przyrost prefiksu](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md) | [`++`](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md) |
| [Zmniejszenie prefiksu](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md) | [`--`](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md) |
| [Uzupełnienie jedynkowe](../cpp/one-s-complement-operator-tilde.md) | [`~`](../cpp/one-s-complement-operator-tilde.md) | **`compl`** |
| [Logiczne not](../cpp/logical-negation-operator-exclpt.md) | [`!`](../cpp/logical-negation-operator-exclpt.md) | **`not`** |
| [negacja jednoargumentowa](../cpp/unary-plus-and-negation-operators-plus-and.md) | [`-`](../cpp/unary-plus-and-negation-operators-plus-and.md) |
| [Operator jednoargumentowy plus](../cpp/unary-plus-and-negation-operators-plus-and.md) | [`+`](../cpp/unary-plus-and-negation-operators-plus-and.md) |
| [Adres](../cpp/address-of-operator-amp.md) | [`&`](../cpp/address-of-operator-amp.md) |
| [Pośredniość](../cpp/indirection-operator-star.md) | [`*`](../cpp/indirection-operator-star.md) |
| [Utwórz obiekt](../cpp/new-operator-cpp.md) | [`new`](../cpp/new-operator-cpp.md) |
| [Zniszcz obiekt](../cpp/delete-operator-cpp.md) | [`delete`](../cpp/delete-operator-cpp.md) |
| [Gruntow](../cpp/cast-operator-parens.md) | [`()`](../cpp/cast-operator-parens.md) |
| **Pierwszeństwo grupy 4, od lewej do prawej łączność** |
| [Wskaźnik do składowej (obiekty lub wskaźniki)](../cpp/pointer-to-member-operators-dot-star-and-star.md) | [`.*`oraz`->*`](../cpp/pointer-to-member-operators-dot-star-and-star.md) |
| **Pierwszeństwo grupy 5, od lewej do prawej łączność** |
| [Mnożenie](../cpp/multiplicative-operators-and-the-modulus-operator.md) | [`*`](../cpp/multiplicative-operators-and-the-modulus-operator.md) |
| [Dział](../cpp/multiplicative-operators-and-the-modulus-operator.md) | [`/`](../cpp/multiplicative-operators-and-the-modulus-operator.md) |
| [Modulo](../cpp/multiplicative-operators-and-the-modulus-operator.md) | [`%`](../cpp/multiplicative-operators-and-the-modulus-operator.md) |
| **Pierwszeństwo grupy 6, od lewej do prawej łączność** |
| [Dodawanie](../cpp/additive-operators-plus-and.md) | [`+`](../cpp/additive-operators-plus-and.md) |
| [Odejmowanie](../cpp/additive-operators-plus-and.md) | [`-`](../cpp/additive-operators-plus-and.md) |
| **Pierwszeństwo grupy 7, od lewej do prawej łączność** |
| [Przesunięcie w lewo](../cpp/left-shift-and-right-shift-operators-input-and-output.md) | [`<<`](../cpp/left-shift-and-right-shift-operators-input-and-output.md) |
| [Przesunięcie w prawo](../cpp/left-shift-and-right-shift-operators-input-and-output.md) | [`>>`](../cpp/left-shift-and-right-shift-operators-input-and-output.md) |
| **Pierwszeństwo grupy 8, od lewej do prawej łączność** |
| [Mniejsze niż](../cpp/relational-operators-equal-and-equal.md) | [`<`](../cpp/relational-operators-equal-and-equal.md) |
| [Większe niż](../cpp/relational-operators-equal-and-equal.md) | [`>`](../cpp/relational-operators-equal-and-equal.md) |
| [Mniejsze niż lub równe](../cpp/relational-operators-equal-and-equal.md) | [`<=`](../cpp/relational-operators-equal-and-equal.md) |
| [Większe niż lub równe](../cpp/relational-operators-equal-and-equal.md) | [`>=`](../cpp/relational-operators-equal-and-equal.md) |
| **Pierwszeństwo grupy 9, od lewej do prawej łączność** |
| [Równość](../cpp/equality-operators-equal-equal-and-exclpt-equal.md) | [`==`](../cpp/equality-operators-equal-equal-and-exclpt-equal.md) |
| [Nierówność](../cpp/equality-operators-equal-equal-and-exclpt-equal.md) | [`!=`](../cpp/equality-operators-equal-equal-and-exclpt-equal.md) | **`not_eq`** |
| **Pierwszeństwo grupy 10 od lewej do prawej łączność** |
| [Bitowe ORAZ](../cpp/bitwise-and-operator-amp.md) | [`&`](../cpp/bitwise-and-operator-amp.md) | **`bitand`** |
| **Pierwszeństwo grupy 11, od lewej do prawej łączność** |
| [Bitowe or wykluczające OR](../cpp/bitwise-exclusive-or-operator-hat.md) | [`^`](../cpp/bitwise-exclusive-or-operator-hat.md) | **`xor`** |
| **Pierwszeństwo grupy 12, od lewej do prawej łączność** |
| [Bitowe alternatywne OR](../cpp/bitwise-inclusive-or-operator-pipe.md) | [`|`](../cpp/bitwise-inclusive-or-operator-pipe.md) | **`bitor`** |
| **Pierwszeństwo grupy 13, od lewej do prawej łączność** |
| [Koniunkcja logiczna i](../cpp/logical-and-operator-amp-amp.md) | [`&&`](../cpp/logical-and-operator-amp-amp.md) | **`and`** |
| **Pierwszeństwo grupy 14, od lewej do prawej łączność** |
| [Logiczne lub](../cpp/logical-or-operator-pipe-pipe.md) | [`||`](../cpp/logical-or-operator-pipe-pipe.md) | **`or`** |
| **Pierwszeństwo grupy 15, od prawej do lewej łączność** |
| [Warunkowe](../cpp/conditional-operator-q.md) | [`? :`](../cpp/conditional-operator-q.md) |
| **Pierwszeństwo grupy 16, od prawej do lewej łączność** |
| [Przypisanie](../cpp/assignment-operators.md) | [`=`](../cpp/assignment-operators.md) |
| [Mnożenie i przypisanie](../cpp/assignment-operators.md) | [`*=`](../cpp/assignment-operators.md) |
| [Dzielenie i przypisanie](../cpp/assignment-operators.md) | [`/=`](../cpp/assignment-operators.md) |
| [Modulo i przypisanie](../cpp/assignment-operators.md) | [`%=`](../cpp/assignment-operators.md) |
| [Dodawanie i przypisanie](../cpp/assignment-operators.md) | [`+=`](../cpp/assignment-operators.md) |
| [Odejmowanie i przypisanie](../cpp/assignment-operators.md) | [`-=`](../cpp/assignment-operators.md) |
| [Przesunięcie bitowe w lewo i przypisanie](../cpp/assignment-operators.md) | [`<<=`](../cpp/assignment-operators.md) |
| [Przesunięcie bitowe w prawo i przypisanie](../cpp/assignment-operators.md) | [`>>=`](../cpp/assignment-operators.md) |
| [Bitowe AND i przypisanie](../cpp/assignment-operators.md) | [`&=`](../cpp/assignment-operators.md) | **`and_eq`** |
| [Bitowe OR alternatywne i przypisanie](../cpp/assignment-operators.md) | [`|=`](../cpp/assignment-operators.md) | **`or_eq`** |
| [Bitowe wykluczające lub przypisanie](../cpp/assignment-operators.md) | [`^=`](../cpp/assignment-operators.md) | **`xor_eq`** |
| **Pierwszeństwo grupy 17, od prawej do lewej łączność** |
| [wyrażenie throw](../cpp/try-throw-and-catch-statements-cpp.md) | [`throw`](../cpp/try-throw-and-catch-statements-cpp.md) |
| **Pierwszeństwo grupy 18, od lewej do prawej łączność** |
| [Przecinek](../cpp/comma-operator.md) | [,](../cpp/comma-operator.md) |

## <a name="see-also"></a>Zobacz także

[Przeładowanie operatora](operator-overloading.md)
