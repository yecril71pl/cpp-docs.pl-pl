---
title: C++ wbudowane operatory, pierwszeństwo i kojarzenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5b40e5ab6cac64edbfdb5ab93c6864d0eacb9e63
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073111"
---
# <a name="c-built-in-operators-precedence-and-associativity"></a>C++ wbudowane operatory, pierwszeństwo i kojarzenie

Język C++ obejmuje wszystkie operatory C i dodaje kilka nowych operatorów. Operatory określają oszacowania wykonywane na jednym lub większej liczbie operandów.

Operator *pierwszeństwo* określa kolejność operacji w wyrażeniach, które zawierają więcej niż jeden operator. Operator *kojarzenie* Określa, czy w wyrażeniu zawierającym wiele operatorów o tym samym pierwszeństwie, operand jest zgrupowany z jednym po lewej stronie lub na jego prawej stronie. W poniższej tabeli przedstawiono pierwszeństwo i łączność operatorów C++ (od najwyższego do najniższego pierwszeństwa). Operatory o tym samym numerze pierwszeństwa mają równe pierwszeństwo, chyba inny stosunek jest jawnie wymuszony przez nawiasy.

### <a name="c-operator-precedence-and-associativity"></a>Pierwszeństwo i łączność operatora C++

|Opis operatora|Operator|
|--------------------------|--------------|
|**Grupy priorytet 1, nie kojarzenie**|
|[Rozpoznawanie zakresu](../cpp/scope-resolution-operator.md)|[::](../cpp/scope-resolution-operator.md)|
|**Pierwszeństwo grupy 2, od lewej do prawej łączność**|
|[Wybór elementu członkowskiego (obiekt lub wskaźnik)](../cpp/member-access-operators-dot-and.md)|[. lub ->](../cpp/member-access-operators-dot-and.md)|
|[Indeks dolny tablicy](../cpp/subscript-operator.md)|[&#91;&#93;](../cpp/subscript-operator.md)|
|[Wywołanie funkcji](../cpp/function-call-operator-parens.md)|[()](../cpp/function-call-operator-parens.md)|
|[Inkrementacja przyrostkowa](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Dekrementacja przyrostkowa](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Nazwa typu](../cpp/typeid-operator.md)|[TypeID](../cpp/typeid-operator.md)|
|[Konwersja typu stałego](../cpp/const-cast-operator.md)|[Operator const_cast](../cpp/const-cast-operator.md)|
|[Konwersja typu dynamicznego](../cpp/dynamic-cast-operator.md)|[dynamic_cast](../cpp/dynamic-cast-operator.md)|
|[Konwersja przez zamianę typu](../cpp/reinterpret-cast-operator.md)|[reinterpret_cast](../cpp/reinterpret-cast-operator.md)|
|[Konwersja typu statycznego](../cpp/static-cast-operator.md)|[static_cast](../cpp/static-cast-operator.md)|
|**Grupa 3 pierwszeństwa, od prawej do lewej łączność**|
|[Rozmiar obiektu lub typu](../cpp/sizeof-operator.md)|[sizeof](../cpp/sizeof-operator.md)|
|[Inkrementacja przedrostkowa](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Dekrementacja przedrostkowa](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Uzupełnienie jedynkowe](../cpp/one-s-complement-operator-tilde.md)|[~](../cpp/one-s-complement-operator-tilde.md)|
|[Logiczne not](../cpp/logical-negation-operator-exclpt.md)|[\!](../cpp/logical-negation-operator-exclpt.md)|
|[Negacja Jednoargumentowa](../cpp/unary-plus-and-negation-operators-plus-and.md)|[-](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Plus jednoargumentowy](../cpp/unary-plus-and-negation-operators-plus-and.md)|[+](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Adres](../cpp/address-of-operator-amp.md)|[&amp;](../cpp/address-of-operator-amp.md)|
|[Operator pośredni](../cpp/indirection-operator-star.md)|[&#42;](../cpp/indirection-operator-star.md)|
|[Tworzenie obiektu](../cpp/new-operator-cpp.md)|[new](../cpp/new-operator-cpp.md)|
|[Zniszczenie obiektu](../cpp/delete-operator-cpp.md)|[delete](../cpp/delete-operator-cpp.md)|
|[Rzutowania](../cpp/cast-operator-parens.md)|[()](../cpp/cast-operator-parens.md)|
|**Pierwszeństwo grupy 4, od lewej do prawej łączność**|
|[Wskaźnik do składowej (obiekty lub wskaźniki)](../cpp/pointer-to-member-operators-dot-star-and-star.md)|[. &#42; lub ->&#42;](../cpp/pointer-to-member-operators-dot-star-and-star.md)|
|**Pierwszeństwo grupy 5, od lewej do prawej łączność**|
|[Mnożenie](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[&#42;](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[Dzielenie](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[/](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[modulo](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[%](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|**Pierwszeństwo grupy 6, od lewej do prawej łączność**|
|[Dodanie](../cpp/additive-operators-plus-and.md)|[+](../cpp/additive-operators-plus-and.md)|
|[Odejmowanie](../cpp/additive-operators-plus-and.md)|[-](../cpp/additive-operators-plus-and.md)|
|**Pierwszeństwo grupy 7, od lewej do prawej łączność**|
|[Przesunięcie w lewo](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[<<](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|[Przesunięcia w prawo](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[>>](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|**Grupa 8 pierwszeństwa, od lewej do prawej łączność**|
|[Mniej niż](../cpp/relational-operators-equal-and-equal.md)|[<](../cpp/relational-operators-equal-and-equal.md)|
|[Większa niż](../cpp/relational-operators-equal-and-equal.md)|[>](../cpp/relational-operators-equal-and-equal.md)|
|[Mniejsze niż lub równe](../cpp/relational-operators-equal-and-equal.md)|[<=](../cpp/relational-operators-equal-and-equal.md)|
|[Większa niż lub równa](../cpp/relational-operators-equal-and-equal.md)|[>=](../cpp/relational-operators-equal-and-equal.md)|
|**Pierwszeństwo grupy 9, od lewej do prawej łączność**|
|[Równość](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[==](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|[Nierówności](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[\!=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|**Pierwszeństwo grupy 10, od lewej do prawej łączność**|
|[Bitowe AND](../cpp/bitwise-and-operator-amp.md)|[&amp;](../cpp/bitwise-and-operator-amp.md)|
|**Pierwszeństwo grupy 11, od lewej do prawej łączność**|
|[Bitowe or wykluczające OR](../cpp/bitwise-exclusive-or-operator-hat.md)|[^](../cpp/bitwise-exclusive-or-operator-hat.md)|
|**Pierwszeństwo grupy 12, od lewej do prawej łączność**|
|[Bitowe alternatywne OR](../cpp/bitwise-inclusive-or-operator-pipe.md)|[&#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)|
|**Pierwszeństwo grupy 13, od lewej do prawej łączność**|
|[Operator logiczny oraz](../cpp/logical-and-operator-amp-amp.md)|[&amp;&amp;](../cpp/logical-and-operator-amp-amp.md)|
|**Pierwszeństwo grupy 14, od lewej do prawej łączność**|
|[Logiczne OR](../cpp/logical-or-operator-pipe-pipe.md)|[&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)|
|**Pierwszeństwo grupy 15, od prawej do lewej łączność**|
|[warunkowe](../cpp/conditional-operator-q.md)|[? :](../cpp/conditional-operator-q.md)|
|**Pierwszeństwo grupy 16, od prawej do lewej łączność**|
|[Przypisanie](../cpp/assignment-operators.md)|[=](../cpp/assignment-operators.md)|
|[Mnożenie i przypisanie](../cpp/assignment-operators.md)|[&#42;=](../cpp/assignment-operators.md)|
|[Dzielenie i przypisanie](../cpp/assignment-operators.md)|[/=](../cpp/assignment-operators.md)|
|[Modulo i przypisanie](../cpp/assignment-operators.md)|[%=](../cpp/assignment-operators.md)|
|[Dodawanie i przypisanie](../cpp/assignment-operators.md)|[+=](../cpp/assignment-operators.md)|
|[Odejmowanie i przypisanie](../cpp/assignment-operators.md)|[-=](../cpp/assignment-operators.md)|
|[Przypisanie przesunięcia w lewo](../cpp/assignment-operators.md)|[<<=](../cpp/assignment-operators.md)|
|[Przypisania przesunięcia w prawo](../cpp/assignment-operators.md)|[>>=](../cpp/assignment-operators.md)|
|[Bitowe and i przypisanie](../cpp/assignment-operators.md)|[&amp;=](../cpp/assignment-operators.md)|
|[Bitowe or alternatywne i przypisanie](../cpp/assignment-operators.md)|[&#124;=](../cpp/assignment-operators.md)|
|[Bitowe or wykluczające i przypisanie](../cpp/assignment-operators.md)|[^=](../cpp/assignment-operators.md)|
|**Pierwszeństwo grupy 17, od prawej do lewej łączność**|
|[wyrażenie throw](../cpp/try-throw-and-catch-statements-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)|
|**Pierwszeństwo grupy 18, od lewej do prawej łączność**|
|[Przecinkami](../cpp/comma-operator.md)|[,](../cpp/comma-operator.md)|

## <a name="see-also"></a>Zobacz także

[Przeładowanie operatora](operator-overloading.md)