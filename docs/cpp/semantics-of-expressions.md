---
title: Semantyka wyrażeń
ms.date: 11/19/2018
helpviewer_keywords:
- grammar, expressions
- expressions [C++], semantics
- expression evaluation
- expression evaluation, about expression evaluation
ms.assetid: 4a792154-533b-48b9-8709-31bfc170f0a7
ms.openlocfilehash: d2ce510478bcf1574429c85f704552e6b73100ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331216"
---
# <a name="semantics-of-expressions"></a>Semantyka wyrażeń

Wyrażenia są obliczane według pierwszeństwa i grupowania ich operatorów. ([Pierwszeństwo i kojarzenie operatorów](../cpp/cpp-built-in-operators-precedence-and-associativity.md) w [konwencje leksykalne](../cpp/lexical-conventions.md), przedstawiono relacje języka C++, operatory nakładają się na wyrażeniach.)

## <a name="order-of-evaluation"></a>Kolejność obliczeń

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

![Kolejność obliczania w wyrażeniach](../cpp/media/vc38zv1.gif "kolejność obliczania w wyrażeniach") <br/>
Kolejność obliczania wyrażenia

Kolejność, w jakiej są oceniane wyrażenia pokazano na rysunku powyżej jest określana przez pierwszeństwo i łączność operatorów:

1. Mnożenia (*) ma najwyższy priorytet, w tym wyrażeniu; Dlatego Podwyrażenie `b * c` jest stosowana jako pierwsza.

1. Dodawania (+) ma następnym największym priorytetem, dlatego `a` zostanie dodany do produktu `b` i `c`.

1. Przesunięcie w lewo (<<) ma najniższy w wyrażeniu, ale istnieją dwa wystąpienia. Operator przesunięcia w lewo grupy od lewej do prawej, po lewej stronie wyrażenia cząstkowego dlatego najpierw ocenione, a następnie po prawej stronie jeden.

Gdy nawiasy są używane do grupowania podwyrażenia, zmieniają pierwszeństwo, a także kolejności, w którym wyrażenie jest obliczane, jak pokazano na poniższej ilustracji.

![Kolejność obliczania wyrażenia w nawiasach](../cpp/media/vc38zv2.gif "kolejność obliczania wyrażenia w nawiasach") <br/>
Kolejność oceny wyrażenia w nawiasach

Wyrażenia, takich jak na rysunku powyżej są obliczane wyłącznie na ich efektów ubocznych — w tym przypadku do przekazywania informacji na urządzeniu standardowe dane wyjściowe.

## <a name="notation-in-expressions"></a>Notacja w wyrażeniach

Język C++ określa niektóre możliwości podczas określania argumentów operacji. W poniższej tabeli przedstawiono typy argumentów operacji dopuszczalne operatorów, które wymagają argumentów operacji typu *typu*.

### <a name="operand-types-acceptable-to-operators"></a>Typy argumentów operacji dopuszczalne operatorów

|Oczekiwano typu|Dozwolone typy|
|-------------------|-------------------|
|*type*|`const` *Typ*<br /> `volatile` *Typ*<br /> *Typ*&<br /> `const` *type*&<br /> `volatile` *type*&<br /> `volatile const` *Typ*<br /> `volatile const` *type*&|
|*Typ* \*|*Typ* \*<br /> `const` *Typ* \*<br /> `volatile` *Typ* \*<br /> `volatile const` *Typ* \*|
|`const` *Typ*|*type*<br /> `const` *Typ*<br />`const` *type*&|
|`volatile` *Typ*|*type*<br /> `volatile` *Typ*<br /> `volatile` *type*&|

Ponieważ powyższych zasad, można go zawsze używać w połączeniu, wskaźnika elementu const do obiektów volatile mogą być dostarczane gdy wskaźnik jest oczekiwany.

## <a name="ambiguous-expressions"></a>Wyrażenie niejednoznaczne

Niektóre wyrażenia są niejednoznaczne w ich znaczenie. Wyrażenia te występują najczęściej, gdy wartość obiektu zostanie zmodyfikowany w więcej niż jeden raz w jednym wyrażeniu. Wyrażenia te zależą od określonej kolejności obliczania, gdy język nie definiuje jedną. Rozważmy następujący przykład:

```
int i = 7;

func( i, ++i );
```

Język C++ nie gwarantuje kolejności, w jakiej są oceniane argumentów dla wywołania funkcji. Dlatego w poprzednim przykładzie `func` może odbierać wartości 7 i 8, lub 8 i 8 dla jego parametrów, w zależności od tego, czy parametry są obliczane od lewej do prawej lub od prawej do lewej.

## <a name="c-sequence-points-microsoft-specific"></a>Punkty sekwencji języka C++ (Microsoft Specific)

Wyrażenie może modyfikować wartość obiektu tylko raz między kolejnymi „punktami sekwencji”.

Definicja języka C++ nie określa obecnie punktów sekwencji. Microsoft C++ używa tych samych punktów sekwencji co standard ANSI C dla dowolnych wyrażeń obejmujących operatory języka C i nieobejmujących przeciążonych operatorów. Gdy operatory są przeciążone, semantyka zmienia się z sekwencjonowania operatora do sekwencjonowania wywołania funkcji. Microsoft C++ używa następujących punktów sekwencji:

- Lewy operand logicznego operatora AND (& &). Lewy operand logicznego operatora AND jest obliczany całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed kontynuowaniem. Nie ma gwarancji, że prawy operand logicznego operatora AND zostanie obliczony.

- Lewy operand logicznego operatora OR (&#124;&#124;). Lewy operand logicznego operatora OR jest obliczany całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed kontynuowaniem. Nie ma gwarancji, że prawy operand logicznego operatora OR zostanie obliczony.

- Lewy operand operatora przecinka. Lewy operand logicznego operatora przecinka jest obliczany całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed kontynuowaniem. Oba operandy operatora przecinka są obliczane zawsze.

- Operator wywołania funkcji. Obliczane jest wyrażenie wywołania funkcji i wszystkie argumenty funkcji, włączając w to argumenty domyślne, a wszystkie efekty uboczne są zakończone przed wejściem do funkcji. Nie ma żadnej określonej kolejności obliczania między argumentami lub wyrażeniem wywołania funkcji.

- Pierwszy operand operatora warunkowego. Pierwszy operand operatora warunkowego jest obliczany całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed kontynuowaniem.

- Koniec pełnej inicjalizacji wyrażenia, taki jak koniec inicjalizacji w instrukcji deklaracji.

- Wyrażenie w instrukcji wyrażenia. Instrukcje wyrażeń składają się z opcjonalnego wyrażenia z następującym po nim średnikiem (;). Wyrażenie jest obliczane całkowicie ze wszystkimi efektami ubocznymi.

- Wyrażenie kontrolujące w instrukcji wyboru (if lub switch). Wyrażenie jest obliczane całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed wykonaniem kodu zależnego od wyboru.

- Wyrażenie kontrolujące instrukcji while lub do. Wyrażenie jest obliczane całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed wykonaniem dowolnej instrukcji z następnej iteracji pętli while lub do.

- Każde z trzech wyrażeń instrukcji for. Każde wyrażenie jest obliczane całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed przeniesieniem do następnego wyrażenia.

- Wyrażenie w instrukcji return. Wyrażenie jest obliczane całkowicie, wraz ze wszystkimi efektami ubocznymi zakończonymi przed zwróceniem sterowania do funkcji wywołującej.

## <a name="see-also"></a>Zobacz także

[Wyrażenia](../cpp/expressions-cpp.md)