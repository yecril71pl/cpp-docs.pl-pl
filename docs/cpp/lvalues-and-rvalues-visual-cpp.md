---
title: 'Wartość kategorie: Lvalues i Rvalues (Visual C++)'
ms.date: 04/06/2018
helpviewer_keywords:
- R-values [C++]
- L-values [C++]
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
ms.openlocfilehash: 74bfac5f5bb56549eee41a5479babf8e71b00aa6
ms.sourcegitcommit: e9568560cdb95e83a8fba1e9bca21ece910d20b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2018
ms.locfileid: "52453888"
---
# <a name="lvalues-and-rvalues-visual-c"></a>Lvalues i Rvalues (Visual C++)

Każde wyrażenie C++ ma typ i należy do *kategorii wartości*. Kategorie wartość stanowią podstawę dla reguł, które kompilatory muszą wykonać podczas tworzenia, kopiowania i przenoszenia obiektów tymczasowych podczas obliczania wyrażenia.

C ++ 17 standardowa definiuje kategorie wartości wyrażenia w następujący sposób:

- A *glvalue* jest wyrażeniem, którego oceny określa tożsamość obiektu, pole bitowe lub funkcji.
- A *prvalue* jest wyrażeniem, którego oceny inicjuje obiekt lub pole bitowe lub oblicza wartość operand operatora, jak określone przez kontekst, w którym jest wyświetlana.
- *Xvalue* jest glvalue, który wskazuje obiekt lub pola bitowego, którego zasoby mogą być ponownie używane (zazwyczaj, ponieważ jest osiągnie koniec okresu jego istnienia). Przykład: Niektóre rodzaje wyrażeń zawierających odwołania rvalue (8.3.2) przynieść xvalues, takie jak wywołania funkcji, którego typem zwracanym jest odwołaniem rvalue lub Rzutowanie na typ odwołania rvalue.
- *L-wartości* jest glvalue, który nie jest xvalue.
- *Rvalue* prvalue lub xvalue.

Na poniższym diagramie przedstawiono relacje między kategoriami:

![Kategorie wartości wyrażenia języka C++](media/value_categories.png "kategorie wartości wyrażenia języka C++")

L-wartości ma adres, który mogą uzyskiwać dostęp do programu. Przykłady wyrażeń l-wartości obejmują nazwy zmiennej, w tym **const** zmienne, elementy tablicy, funkcja wywołania, które zwracają odwołanie lvalue, pól bitowych, Unii i elementy członkowskie klasy.

Wyrażenie prvalue nie ma żadnego adresu, który jest dostępny dla programu. Przykłady wyrażeń prvalue literały, wywołania funkcji, które zwracają typ niebędący odniesieniem i obiekty tymczasowe, które są tworzone podczas evalution wyrażenia, ale dostępna tylko przez kompilator.

Wyrażenie wartości x równej ma adres, nie będą dostępne przez program, ale może służyć do zainicjowania odwołanie rvalue, która zapewnia dostęp do wyrażenia. Przykłady obejmują wywołania funkcji, które zwracają odwołanie rvalue, a indeks dolny tablicy, elementu członkowskiego i wskaźnik do wyrażenia elementu członkowskiego gdzie tablicy lub obiektu jest odwołaniem rvalue.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano kilka poprawne i niepoprawne wartości użycia lvalues i rvalues:

```cpp
// lvalues_and_rvalues2.cpp
int main()
{
    int i, j, *p;

    // Correct usage: the variable i is an lvalue and the literal 7 is a prvalue.
    i = 7;

    // Incorrect usage: The left operand must be an lvalue (C2106).`j * 4` is a prvalue.
    7 = i; // C2106
    j * 4 = 7; // C2106

    // Correct usage: the dereferenced pointer is an lvalue.
    *p = i;

    // Correct usage: the conditional operator returns an lvalue.
    ((i < 3) ? i : j) = 7;
    
    // Incorrect usage: the constant ci is a non-modifiable lvalue (C3892).
    const int ci = 7;
    ci = 9; // C3892
}
```

> [!NOTE]
> Przykłady w tym temacie pokazują poprawne i niepoprawne użycie, gdy operatory nie są przeciążone. Przeciążając operatory, aby włączyć wyrażenia takie jak `j * 4` l-wartością.

Warunki *l-wartości* i *rvalue* są często używane przy odwoływaniu się odwołania do obiektu. Aby uzyskać więcej informacji na temat odwołań, zobacz [l-wartości Reference Declarator: &](../cpp/lvalue-reference-declarator-amp.md) i [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Zobacz także

[Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)<br/>
[Deklarator odwołania do wartości L: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Deklarator odwołania do wartości R: &&](../cpp/rvalue-reference-declarator-amp-amp.md)
