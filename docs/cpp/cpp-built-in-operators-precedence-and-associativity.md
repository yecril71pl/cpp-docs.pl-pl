---
title: C++Wbudowane operatory, pierwszeństwo i łączność
ms.date: 11/04/2016
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
ms.openlocfilehash: 36e7ce77e24366be10b75f5bb4f8830363594301
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180410"
---
# <a name="c-built-in-operators-precedence-and-associativity"></a>C++Wbudowane operatory, pierwszeństwo i łączność

Język C++ obejmuje wszystkie operatory C i dodaje kilka nowych operatorów. Operatory określają oszacowania wykonywane na jednym lub większej liczbie operandów.

*Pierwszeństwo* operatorów określa kolejność operacji w wyrażeniach, które zawierają więcej niż jeden operator. Operator *łączność* określa, czy w wyrażeniu zawierającym wiele operatorów z tym samym pierwszeństwem operand jest zgrupowany z jedną po lewej lub po prawej stronie. W poniższej tabeli przedstawiono pierwszeństwo i łączność operatorów C++ (od najwyższego do najniższego pierwszeństwa). Operatory o tym samym numerze pierwszeństwa mają równe pierwszeństwo, chyba inny stosunek jest jawnie wymuszony przez nawiasy.

### <a name="c-operator-precedence-and-associativity"></a>Pierwszeństwo i łączność operatora C++

|Opis operatora|Operator|
|--------------------------|--------------|
|**Pierwszeństwo grupy 1, brak łączność**|
|[Rozwiązanie zakresu](../cpp/scope-resolution-operator.md)|[::](../cpp/scope-resolution-operator.md)|
|**Pierwszeństwo grupy 2, od lewej do prawej łączność**|
|[Wybór elementu członkowskiego (obiekt lub wskaźnik)](../cpp/member-access-operators-dot-and.md)|[. lub >](../cpp/member-access-operators-dot-and.md)|
|[Indeks dolny tablicy](../cpp/subscript-operator.md)|[&#91;&#93;](../cpp/subscript-operator.md)|
|[Wywołanie funkcji](../cpp/function-call-operator-parens.md)|[()](../cpp/function-call-operator-parens.md)|
|[Przyrost Przyrostkowy](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Zmniejszenie przyrostu](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Nazwa typu](../cpp/typeid-operator.md)|[typeid](../cpp/typeid-operator.md)|
|[Konwersja typu stałego](../cpp/const-cast-operator.md)|[const_cast](../cpp/const-cast-operator.md)|
|[Konwersja typu dynamicznego](../cpp/dynamic-cast-operator.md)|[dynamic_cast](../cpp/dynamic-cast-operator.md)|
|[Konwersja typu reinterpretowanego](../cpp/reinterpret-cast-operator.md)|[reinterpret_cast](../cpp/reinterpret-cast-operator.md)|
|[Konwersja typu statycznego](../cpp/static-cast-operator.md)|[static_cast](../cpp/static-cast-operator.md)|
|**Pierwszeństwo grupy 3, od prawej do lewej łączność**|
|[Rozmiar obiektu lub typu](../cpp/sizeof-operator.md)|[sizeof](../cpp/sizeof-operator.md)|
|[Przyrost prefiksu](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Zmniejszenie prefiksu](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Uzupełnienie jednego](../cpp/one-s-complement-operator-tilde.md)|[~](../cpp/one-s-complement-operator-tilde.md)|
|[Logiczne not](../cpp/logical-negation-operator-exclpt.md)|[!](../cpp/logical-negation-operator-exclpt.md)|
|[Jednoargumentowa Negacja](../cpp/unary-plus-and-negation-operators-plus-and.md)|[-](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Jednoargumentowy Plus](../cpp/unary-plus-and-negation-operators-plus-and.md)|[+](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Adres-z](../cpp/address-of-operator-amp.md)|[&amp;](../cpp/address-of-operator-amp.md)|
|[Pośredni](../cpp/indirection-operator-star.md)|[&#42;](../cpp/indirection-operator-star.md)|
|[Utwórz obiekt](../cpp/new-operator-cpp.md)|[new](../cpp/new-operator-cpp.md)|
|[Zniszcz obiekt](../cpp/delete-operator-cpp.md)|[usuwanie](../cpp/delete-operator-cpp.md)|
|[Gruntow](../cpp/cast-operator-parens.md)|[()](../cpp/cast-operator-parens.md)|
|**Pierwszeństwo grupy 4, od lewej do prawej łączność**|
|[Wskaźnik do składowej (obiekty lub wskaźniki)](../cpp/pointer-to-member-operators-dot-star-and-star.md)|[. &#42; lub >&#42;](../cpp/pointer-to-member-operators-dot-star-and-star.md)|
|**Pierwszeństwo grupy 5, od lewej do prawej łączność**|
|[Mnożenia](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[&#42;](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[Przegrod](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[/](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[Moduł](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[%](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|**Pierwszeństwo grupy 6, od lewej do prawej łączność**|
|[Dodatkowo](../cpp/additive-operators-plus-and.md)|[+](../cpp/additive-operators-plus-and.md)|
|[Odejmowania](../cpp/additive-operators-plus-and.md)|[-](../cpp/additive-operators-plus-and.md)|
|**Pierwszeństwo grupy 7, od lewej do prawej łączność**|
|[Przesuń w lewo](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[<<](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|[Przesuń w prawo](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[>>](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|**Pierwszeństwo grupy 8, od lewej do prawej łączność**|
|[Mniejsze niż](../cpp/relational-operators-equal-and-equal.md)|[<](../cpp/relational-operators-equal-and-equal.md)|
|[Większe niż](../cpp/relational-operators-equal-and-equal.md)|[>](../cpp/relational-operators-equal-and-equal.md)|
|[Mniejsze niż lub równe](../cpp/relational-operators-equal-and-equal.md)|[<=](../cpp/relational-operators-equal-and-equal.md)|
|[Większe niż lub równe](../cpp/relational-operators-equal-and-equal.md)|[>=](../cpp/relational-operators-equal-and-equal.md)|
|**Pierwszeństwo grupy 9, od lewej do prawej łączność**|
|[Kryteri](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[==](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|[Nierówności](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[!=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|**Pierwszeństwo grupy 10 od lewej do prawej łączność**|
|[Bitowe i](../cpp/bitwise-and-operator-amp.md)|[&amp;](../cpp/bitwise-and-operator-amp.md)|
|**Pierwszeństwo grupy 11, od lewej do prawej łączność**|
|[Bitowe wykluczające or](../cpp/bitwise-exclusive-or-operator-hat.md)|[^](../cpp/bitwise-exclusive-or-operator-hat.md)|
|**Pierwszeństwo grupy 12, od lewej do prawej łączność**|
|[Bitowe włącznie lub](../cpp/bitwise-inclusive-or-operator-pipe.md)|[&#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)|
|**Pierwszeństwo grupy 13, od lewej do prawej łączność**|
|[Koniunkcja logiczna i](../cpp/logical-and-operator-amp-amp.md)|[&amp;&amp;](../cpp/logical-and-operator-amp-amp.md)|
|**Pierwszeństwo grupy 14, od lewej do prawej łączność**|
|[Logiczne lub](../cpp/logical-or-operator-pipe-pipe.md)|[&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)|
|**Pierwszeństwo grupy 15, od prawej do lewej łączność**|
|[Warunk](../cpp/conditional-operator-q.md)|[? :](../cpp/conditional-operator-q.md)|
|**Pierwszeństwo grupy 16, od prawej do lewej łączność**|
|[Przypisanie](../cpp/assignment-operators.md)|[=](../cpp/assignment-operators.md)|
|[Przypisanie mnożenia](../cpp/assignment-operators.md)|[&#42;=](../cpp/assignment-operators.md)|
|[Przypisanie dzielenia](../cpp/assignment-operators.md)|[/=](../cpp/assignment-operators.md)|
|[Przypisanie modulo](../cpp/assignment-operators.md)|[%=](../cpp/assignment-operators.md)|
|[Przypisanie dodawania](../cpp/assignment-operators.md)|[+=](../cpp/assignment-operators.md)|
|[Przypisanie odejmowania](../cpp/assignment-operators.md)|[-=](../cpp/assignment-operators.md)|
|[Przypisanie przesunięcia w lewo](../cpp/assignment-operators.md)|[<<=](../cpp/assignment-operators.md)|
|[Przypisanie do prawej strony](../cpp/assignment-operators.md)|[>>=](../cpp/assignment-operators.md)|
|[Bitowe i przypisanie](../cpp/assignment-operators.md)|[&amp;=](../cpp/assignment-operators.md)|
|[Bitowe włącznie lub przypisanie](../cpp/assignment-operators.md)|[&#124;=](../cpp/assignment-operators.md)|
|[Bitowe wykluczające lub przypisanie](../cpp/assignment-operators.md)|[^=](../cpp/assignment-operators.md)|
|**Pierwszeństwo grupy 17, od prawej do lewej łączność**|
|[wyrażenie throw](../cpp/try-throw-and-catch-statements-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)|
|**Pierwszeństwo grupy 18, od lewej do prawej łączność**|
|[Pliku](../cpp/comma-operator.md)|[,](../cpp/comma-operator.md)|

## <a name="see-also"></a>Zobacz też

[Przeładowanie operatora](operator-overloading.md)
