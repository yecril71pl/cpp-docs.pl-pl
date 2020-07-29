---
title: Wyrażenia podstawowe
ms.date: 11/04/2016
helpviewer_keywords:
- primary expressions
- expressions [C++], name
- expressions [C++], literal
- expressions [C++], primary
- expressions [C++], qualified names
ms.assetid: 8ef9a814-6058-4b93-9b6e-e8eb8350b1ca
ms.openlocfilehash: c827f811813091abc62d07f12ac387bc2a0a0cc5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231146"
---
# <a name="primary-expressions"></a>Wyrażenia podstawowe

Wyrażenia podstawowe są blokami konstrukcyjnymi bardziej złożonych wyrażeń. Są to literały, nazwy i nazwy kwalifikowane przez operator rozpoznawania zakresu ( `::` ).  Wyrażenie podstawowe może mieć jedną z następujących form:

```
literal
this
name
::name ( expression )
```

*Literał* jest stałym wyrażeniem podstawowym. Jego typ zależy od postaci jego specyfikacji. Aby uzyskać pełne informacje na temat określania literałów, zobacz [literały](../cpp/numeric-boolean-and-pointer-literals-cpp.md) .

**`this`** Słowo kluczowe jest wskaźnikiem do obiektu klasy. Jest on dostępny w ramach niestatycznych funkcji składowych i wskazuje na wystąpienie klasy, dla której wywołano funkcję. **`this`** Nie można użyć słowa kluczowego poza treścią funkcji składowej klasy.

Typ **`this`** wskaźnika to `type` ** \* stała** (gdzie `type` to nazwa klasy) w funkcjach, które nie modyfikują **`this`** wskaźnika. Poniższy przykład przedstawia deklaracje funkcji składowych i typy **`this`** :

```cpp
// expre_Primary_Expressions.cpp
// compile with: /LD
class Example
{
public:
    void Func();          //  * const this
    void Func() const;    //  const * const this
    void Func() volatile; //  volatile * const this
};
```

Zobacz [ten wskaźnik](this-pointer.md) , aby uzyskać więcej informacji na temat modyfikowania typu **`this`** wskaźnika.

Operator rozpoznawania zakresu ( `::` ), po którym następuje nazwa, stanowi wyrażenie podstawowe.  Nazwy te muszą być nazwami w zakresie globalnym, a nie nazwami elementów członkowskich.  Typ tego wyrażenia zależy od deklaracji nazwy. Jest to wartość l (to znaczy, że może być wyświetlany na lewej stronie wyrażenia operatora przypisania), jeśli nazwa deklarująca to wartość l. Operator rozpoznawania zakresu umożliwia odwoływanie się do globalnej nazwy, nawet jeśli ta nazwa jest ukryta w bieżącym zakresie. Zobacz [zakres](../cpp/scope-visual-cpp.md) , aby zapoznać się z przykładem użycia operatora rozpoznawania zakresu.

Wyrażenie w nawiasach jest wyrażeniem podstawowym, którego typ i wartość są identyczne jak wyrażenia bez nawiasów. Jest to wartość l, jeśli wyrażenie bez nawiasów jest wartością l.

Przykłady wyrażeń podstawowych:

```cpp
100 // literal
'c' // literal
this // in a member function, a pointer to the class instance
::func // a global function
::operator + // a global operator function
::A::B // a global qualified name
( i + 1 ) // a parenthesized expression
```

Poniższe przykłady są uznawane za *nazwy*, a więc wyrażenia podstawowe w różnych formach:

```cpp
MyClass // a identifier
MyClass::f // a qualified name
operator = // an operator function name
operator char* // a conversion operator function name
~MyClass // a destructor name
A::B   // a qualified name
A<int> // a template id
```

## <a name="see-also"></a>Zobacz także

[Typy wyrażeń](../cpp/types-of-expressions.md)
