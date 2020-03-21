---
title: 'Kategorie wartości: lvalues i rvalues (C++)'
ms.date: 05/07/2019
helpviewer_keywords:
- R-values [C++]
- L-values [C++]
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
ms.openlocfilehash: 23625ddf44d16a4dc408b87f27b9cdfba7a9cbd4
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077237"
---
# <a name="lvalues-and-rvalues-c"></a>Lvalues i Rvalues (C++)

Każde C++ wyrażenie ma typ i należy do *kategorii wartości*. Kategorie wartości są podstawą reguł, które kompilatorzy muszą wykonać podczas tworzenia, kopiowania i przemieszczania obiektów tymczasowych podczas obliczania wyrażenia.

Standard C++ 17 definiuje kategorie wartości wyrażeń w następujący sposób:

- *Glvalue* jest wyrażeniem, którego Ocena Określa tożsamość obiektu, pole bitowe lub funkcję.
- *Wartością prvalue bez* jest wyrażeniem, którego Ocena inicjuje obiekt lub pole bitowe lub oblicza wartość operandu operatora, zgodnie z opisem w kontekście, w którym występuje.
- *XValue* to glvalue, który oznacza obiekt lub pole bitowe, którego zasoby mogą być ponownie używane (zazwyczaj ponieważ zbliża się do końca okresu istnienia). Przykład: niektóre rodzaje wyrażeń, w tym odwołania rvalue (8.3.2), dają XValues, takie jak wywołanie funkcji, której zwracany typ to odwołanie rvalue lub rzutowanie na typ referencyjny rvalue.
- *Lvalue* to glvalue, który nie jest XValue.
- *Rvalue* to wartością prvalue bez lub XValue.

Na poniższym diagramie przedstawiono relacje między kategoriami:

![C++Kategorie wartości wyrażenia](media/value_categories.png "C++Kategorie wartości wyrażenia")

Lvalue ma adres, do którego Twój program może uzyskać dostęp. Przykłady wyrażeń lvalue zawierają nazwy zmiennych, w tym zmienne **stałe** , elementy tablicy, wywołania funkcji, które zwracają odwołanie lvalue, pola bitowe, Unii i składowe klas.

Wyrażenie wartością prvalue bez nie ma adresu, który jest dostępny dla programu. Przykłady wyrażeń wartością prvalue bez obejmują literały, wywołania funkcji, które zwracają typ niebędący odwołaniem i obiekty tymczasowe, które są tworzone podczas wyrażenia evalution, ale dostępne tylko dla kompilatora.

Wyrażenie XValue ma adres, który nie jest już dostępny dla programu, ale może służyć do inicjowania odwołania rvalue, które zapewnia dostęp do wyrażenia. Przykłady obejmują wywołania funkcji, które zwracają odwołanie rvalue, oraz indeks dolny tablicy, składowej i wskaźnika do wyrażeń elementów członkowskich, w których tablica lub obiekt jest odwołaniem rvalue.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje kilka prawidłowych i nieprawidłowych użycia lvalues i rvalues:

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
> W przykładach w tym temacie przedstawiono poprawne i nieprawidłowe użycie, gdy operatory nie są przeciążone. Przez przeciążanie operatorów można utworzyć wyrażenie, takie jak `j * 4` lvalue.

Warunki *lvalue* i *rvalue* są często używane podczas odwoływania się do odwołań do obiektów. Aby uzyskać więcej informacji na temat odwołań, zobacz [lvalue Reference deklarator: &](../cpp/lvalue-reference-declarator-amp.md) i [rvalue reference deklarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Zobacz też

[Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)<br/>
[Deklarator odwołania do wartości L: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Deklarator odwołania do wartości R: &&](../cpp/rvalue-reference-declarator-amp-amp.md)
