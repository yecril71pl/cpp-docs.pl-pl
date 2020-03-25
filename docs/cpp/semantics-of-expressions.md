---
title: Semantyka wyrażeń
ms.date: 11/19/2018
helpviewer_keywords:
- grammar, expressions
- expressions [C++], semantics
- expression evaluation
- expression evaluation, about expression evaluation
ms.assetid: 4a792154-533b-48b9-8709-31bfc170f0a7
ms.openlocfilehash: 5213fc7972f3a2590ceac5038a7b5e07495df594
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178852"
---
# <a name="semantics-of-expressions"></a>Semantyka wyrażeń

Wyrażenia są oceniane zgodnie z pierwszeństwem i grupowaniem operatorów. ([Pierwszeństwo operatorów i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md) w [konwencjach leksykalnych](../cpp/lexical-conventions.md)pokazuje relacje C++ operatorów nakładających się na wyrażeniach).

## <a name="order-of-evaluation"></a>Kolejność obliczania

Rozważmy następujący przykład:

```cpp
// Order_of_Evaluation.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main()
{
    int a = 2, b = 4, c = 9;

    cout << a + b * c << "\n";
    cout << a + (b * c) << "\n";
    cout << (a + b) * c << "\n";
}
```

```Output
38
38
54
```

![Kolejność obliczania w wyrażeniu](../cpp/media/vc38zv1.gif "Kolejność obliczania w wyrażeniu") <br/>
Wyrażenie — kolejność szacowania

Kolejność, w której wyrażenie pokazane na powyższej ilustracji jest oceniane, zależy od pierwszeństwa i łącznośća operatorów:

1. Mnożenie (*) ma najwyższy priorytet w tym wyrażeniu; w związku z tym Podwyrażenie `b * c` jest oceniane jako pierwsze.

1. Dodanie (+) ma wyższy priorytet, więc `a` jest dodawane do produktu `b` i `c`.

1. Przesunięcie w lewo (< <) ma najniższy priorytet w wyrażeniu, ale istnieją dwa wystąpienia. Ponieważ operator przesunięcia w lewo — od lewej do prawej, lewe Podwyrażenie jest oceniane jako pierwsze, a następnie z prawej strony.

Gdy nawiasy są używane do grupowania podwyrażeń, zmieniają pierwszeństwo, a także kolejność, w jakiej wyrażenie jest oceniane, jak pokazano na poniższej ilustracji.

![Kolejność obliczania wyrażenia z nawiasami](../cpp/media/vc38zv2.gif "Kolejność obliczania wyrażenia z nawiasami") <br/>
Wyrażenie — kolejność szacowania z nawiasami

Wyrażenia, takie jak te na powyższym rysunku, są oceniane wyłącznie dla ich efektów ubocznych — w tym przypadku do transferu informacji na standardowe urządzenie wyjściowe.

## <a name="notation-in-expressions"></a>Notacja w wyrażeniach

C++ Język określa pewne niezgodności podczas określania operandów. W poniższej tabeli przedstawiono typy operandów akceptowalnych dla operatorów, które wymagają operandów *typu Type.*

### <a name="operand-types-acceptable-to-operators"></a>Typy operandów akceptowalne dla operatorów

|Oczekiwano typu|Dozwolone typy|
|-------------------|-------------------|
|*type*|*typ* `const`<br /> *typ* `volatile`<br /> *typ*&<br /> *typ* `const`&<br /> *typ* `volatile`&<br /> *typ* `volatile const`<br /> *typ* `volatile const`&|
|*typ* \*|*typ* \*<br /> *typ* `const` \*<br /> *typ* `volatile` \*<br /> *typ* `volatile const` \*|
|*typ* `const`|*type*<br /> *typ* `const`<br />*typ* `const`&|
|*typ* `volatile`|*type*<br /> *typ* `volatile`<br /> *typ* `volatile`&|

Ze względu na to, że poprzedzające reguły mogą być używane w połączeniu, można dostarczyć stały wskaźnik do obiektu nietrwałego, gdzie oczekiwany jest wskaźnik.

## <a name="ambiguous-expressions"></a>Wyrażenia niejednoznaczne

Niektóre wyrażenia są niejednoznaczne w ich znaczenie. Te wyrażenia występują najczęściej, gdy wartość obiektu jest modyfikowana więcej niż raz w tym samym wyrażeniu. Wyrażenia te opierają się na określonej kolejności oceny, w której język nie definiuje go. Rozważmy następujący przykład:

```
int i = 7;

func( i, ++i );
```

C++ Język nie gwarantuje kolejności, w której są oceniane argumenty wywołania funkcji. W związku z tym w powyższym przykładzie `func` może otrzymać wartości 7 i 8 lub 8 i 8 dla swoich parametrów, w zależności od tego, czy parametry są oceniane od lewej do prawej lub od prawej do lewej.

## <a name="c-sequence-points-microsoft-specific"></a>C++punkty sekwencji (specyficzne dla firmy Microsoft)

Wyrażenie może modyfikować wartość obiektu tylko raz między kolejnymi „punktami sekwencji”.

Definicja języka C++ nie określa obecnie punktów sekwencji. Microsoft C++ używa tych samych punktów sekwencji co standard ANSI C dla dowolnych wyrażeń obejmujących operatory języka C i nieobejmujących przeciążonych operatorów. Gdy operatory są przeciążone, semantyka zmienia się z sekwencjonowania operatora do sekwencjonowania wywołania funkcji. Microsoft C++ używa następujących punktów sekwencji:

- Lewy operand operatora logicznego AND (& &). Lewy operand logicznego operatora AND jest obliczany całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed kontynuowaniem. Nie ma gwarancji, że prawy operand logicznego operatora AND zostanie obliczony.

- Lewy operand operatora logicznego OR (&#124;&#124;). Lewy operand logicznego operatora OR jest obliczany całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed kontynuowaniem. Nie ma gwarancji, że prawy operand logicznego operatora OR zostanie obliczony.

- Lewy operand operatora przecinka. Lewy operand logicznego operatora przecinka jest obliczany całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed kontynuowaniem. Oba operandy operatora przecinka są obliczane zawsze.

- Operator wywołania funkcji. Obliczane jest wyrażenie wywołania funkcji i wszystkie argumenty funkcji, włączając w to argumenty domyślne, a wszystkie efekty uboczne są zakończone przed wejściem do funkcji. Nie ma żadnej określonej kolejności obliczania między argumentami lub wyrażeniem wywołania funkcji.

- Pierwszy operand operatora warunkowego. Pierwszy operand operatora warunkowego jest obliczany całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed kontynuowaniem.

- Koniec pełnej inicjalizacji wyrażenia, taki jak koniec inicjalizacji w instrukcji deklaracji.

- Wyrażenie w instrukcji wyrażenia. Instrukcje wyrażeń składają się z opcjonalnego wyrażenia z następującym po nim średnikiem (;). Wyrażenie jest obliczane całkowicie ze wszystkimi efektami ubocznymi.

- Wyrażenie kontrolujące w instrukcji wyboru (if lub switch). Wyrażenie jest obliczane całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed wykonaniem kodu zależnego od wyboru.

- Wyrażenie kontrolujące instrukcji while lub do. Wyrażenie jest obliczane całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed wykonaniem dowolnej instrukcji z następnej iteracji pętli while lub do.

- Każde z trzech wyrażeń instrukcji for. Każde wyrażenie jest obliczane całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed przeniesieniem do następnego wyrażenia.

- Wyrażenie w instrukcji return. Wyrażenie jest obliczane całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed zwróceniem sterowania do funkcji wywołującej.

## <a name="see-also"></a>Zobacz też

[Wyrażenia](../cpp/expressions-cpp.md)
