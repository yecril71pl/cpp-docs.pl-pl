---
title: "Operatory C++ wbudowanych, priorytet i łączność | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
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
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7a286be3d29e22cc3bae3d34241f08735f5f7b0b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="c-built-in-operators-precedence-and-associativity"></a>Operatory C++ wbudowanych, priorytet i łączność

Język C++ obejmuje wszystkie operatory C i dodaje kilka nowych operatorów. Operatory określają oszacowania wykonywane na jednym lub większej liczbie operandów.

Operator *pierwszeństwo* określa kolejność operacji w wyrażeniach zawierających więcej niż jeden operator. Operator *kojarzenie* Określa, czy w wyrażeniu zawiera wiele operatorów z tym samym ustawieniem pierwszeństwa, operand jest zgrupowana za pomocą jednego po lewej stronie lub na po jego prawej stronie. W poniższej tabeli przedstawiono pierwszeństwo i łączność operatorów C++ (od najwyższego do najniższego pierwszeństwa). Operatory o tym samym numerze pierwszeństwa mają równe pierwszeństwo, chyba inny stosunek jest jawnie wymuszony przez nawiasy.

### <a name="c-operator-precedence-and-associativity"></a>Pierwszeństwo i łączność operatora C++

|Opis operatora|Operator|
|--------------------------|--------------|
|**Grupa 1 pierwszeństwa, nie łączność**|
|[Rozpoznawanie zakresów](../cpp/scope-resolution-operator.md)|[::](../cpp/scope-resolution-operator.md)|
|**Od lewej do prawej kojarzenie priorytet grupy 2**|
|[Wybór elementu członkowskiego (obiekt lub wskaźnik)](../cpp/member-access-operators-dot-and.md)|[. lub ->](../cpp/member-access-operators-dot-and.md)|
|[Indeks dolny tablicy](../cpp/subscript-operator.md)|[&#91;&#93;](../cpp/subscript-operator.md)|
|[Wywołania funkcji](../cpp/function-call-operator-parens.md)|[()](../cpp/function-call-operator-parens.md)|
|[Operatory przyrostka inkrementacji](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Dekrementacji przyrostka](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Nazwa typu](../cpp/typeid-operator.md)|[TypeID](../cpp/typeid-operator.md)|
|[Konwersja typu stałej](../cpp/const-cast-operator.md)|[Operator const_cast](../cpp/const-cast-operator.md)|
|[Konwersja z typu dynamicznego](../cpp/dynamic-cast-operator.md)|[dynamic_cast](../cpp/dynamic-cast-operator.md)|
|[Konwersja typów reinterpreted](../cpp/reinterpret-cast-operator.md)|[reinterpret_cast](../cpp/reinterpret-cast-operator.md)|
|[Konwersja typów statycznych](../cpp/static-cast-operator.md)|[static_cast](../cpp/static-cast-operator.md)|
|**Pierwszeństwo grupa 3, od prawej do lewej łączność**|
|[Rozmiar obiektu lub typu](../cpp/sizeof-operator.md)|[sizeof](../cpp/sizeof-operator.md)|
|[Przyrost prefiksu](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Prefiks dekrementacji](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[Osoby dopełnienia](../cpp/one-s-complement-operator-tilde.md)|[~](../cpp/one-s-complement-operator-tilde.md)|
|[Negacja](../cpp/logical-negation-operator-exclpt.md)|[!](../cpp/logical-negation-operator-exclpt.md)|
|[Jednoargumentowy negacji](../cpp/unary-plus-and-negation-operators-plus-and.md)|[-](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Jednoargumentowe plus](../cpp/unary-plus-and-negation-operators-plus-and.md)|[+](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[Address-of](../cpp/address-of-operator-amp.md)|[&amp;](../cpp/address-of-operator-amp.md)|
|[Operator pośredni](../cpp/indirection-operator-star.md)|[&#42;](../cpp/indirection-operator-star.md)|
|[Tworzenie obiektu](../cpp/new-operator-cpp.md)|[Nowy](../cpp/new-operator-cpp.md)|
|[Zniszczyć obiektu](../cpp/delete-operator-cpp.md)|[Usuń](../cpp/delete-operator-cpp.md)|
|[Rzutowania](../cpp/cast-operator-parens.md)|[()](../cpp/cast-operator-parens.md)|
|**Priorytet grupy 4, od lewej do prawej łączność**|
|[Wskaźnik do-elementu członkowskiego (obiekty lub wskaźniki)](../cpp/pointer-to-member-operators-dot-star-and-star.md)|[. &#42; lub -> &#42;](../cpp/pointer-to-member-operators-dot-star-and-star.md)|
|**Priorytet grupy 5, od lewej do prawej łączność**|
|[Mnożenia](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[&#42;](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[Dzielenie](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[/](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[Modulo](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[%](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|**Priorytet grupy 6, od lewej do prawej łączność**|
|[Dodanie](../cpp/additive-operators-plus-and.md)|[+](../cpp/additive-operators-plus-and.md)|
|[Odejmowanie](../cpp/additive-operators-plus-and.md)|[-](../cpp/additive-operators-plus-and.md)|
|**Priorytet grupy 7, od lewej do prawej łączność**|
|[Przesunięcia w lewo](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[<<](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|[Przesunięcia w prawo](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[>>](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|**Priorytet grupy 8, od lewej do prawej łączność**|
|[Mniej niż](../cpp/relational-operators-equal-and-equal.md)|[<](../cpp/relational-operators-equal-and-equal.md)|
|[Większa niż](../cpp/relational-operators-equal-and-equal.md)|[>](../cpp/relational-operators-equal-and-equal.md)|
|[Mniejsze niż lub równe](../cpp/relational-operators-equal-and-equal.md)|[<=](../cpp/relational-operators-equal-and-equal.md)|
|[Większe lub równe](../cpp/relational-operators-equal-and-equal.md)|[>=](../cpp/relational-operators-equal-and-equal.md)|
|**Priorytet grupy 9, od lewej do prawej łączność**|
|[Równości](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[==](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|[Nierówności](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[!=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|**Od lewej do prawej kojarzenie pierwszeństwo grupy 10**|
|[Iloczynu bitowego AND](../cpp/bitwise-and-operator-amp.md)|[&amp;](../cpp/bitwise-and-operator-amp.md)|
|**Priorytet grupy 11, od lewej do prawej łączność**|
|[Operator wyłączny OR](../cpp/bitwise-exclusive-or-operator-hat.md)|[^](../cpp/bitwise-exclusive-or-operator-hat.md)|
|**Priorytet grupy 12, od lewej do prawej łączność**|
|[Operator OR włącznie](../cpp/bitwise-inclusive-or-operator-pipe.md)|[&#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)|
|**Priorytet grupy 13, od lewej do prawej łączność**|
|[Logiczny AND](../cpp/logical-and-operator-amp-amp.md)|[&amp;&amp;](../cpp/logical-and-operator-amp-amp.md)|
|**Priorytet grupy 14, od lewej do prawej łączność**|
|[Logiczne lub](../cpp/logical-or-operator-pipe-pipe.md)|[&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)|
|**Priorytet grupy 15, od prawej do lewej łączność**|
|[Warunkowe](../cpp/conditional-operator-q.md)|[? :](../cpp/conditional-operator-q.md)|
|**Priorytet grupy 16, od prawej do lewej łączność**|
|[Przypisania](../cpp/assignment-operators.md)|[=](../cpp/assignment-operators.md)|
|[Przypisania mnożenia](../cpp/assignment-operators.md)|[&#42;=](../cpp/assignment-operators.md)|
|[Przypisania dzielenia](../cpp/assignment-operators.md)|[/=](../cpp/assignment-operators.md)|
|[Przypisanie modulo](../cpp/assignment-operators.md)|[%=](../cpp/assignment-operators.md)|
|[Dodanie przypisania](../cpp/assignment-operators.md)|[+=](../cpp/assignment-operators.md)|
|[Przypisanie odejmowania](../cpp/assignment-operators.md)|[-=](../cpp/assignment-operators.md)|
|[Przypisania przesunięcia w lewo](../cpp/assignment-operators.md)|[<<=](../cpp/assignment-operators.md)|
|[Przypisania przesunięcia w prawo](../cpp/assignment-operators.md)|[>>=](../cpp/assignment-operators.md)|
|[Operatory przypisania AND](../cpp/assignment-operators.md)|[&amp;=](../cpp/assignment-operators.md)|
|[Operator przypisania OR włącznie](../cpp/assignment-operators.md)|[&#124;=](../cpp/assignment-operators.md)|
|[Operator przypisania OR wyłączne](../cpp/assignment-operators.md)|[^=](../cpp/assignment-operators.md)|
|**Priorytet grupy 17, od prawej do lewej łączność**|
|[wyrażenie throw](../cpp/try-throw-and-catch-statements-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)|
|**Priorytet grupy 18, od lewej do prawej łączność**|
|[Przecinkami](../cpp/comma-operator.md)|[,](../cpp/comma-operator.md)|

## <a name="see-also"></a>Zobacz też

[Przeładowanie operatora](operator-overloading.md)


