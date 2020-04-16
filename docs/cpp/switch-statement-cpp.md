---
title: switchwyciąg (C++)
description: Odwołanie do standardowej switch instrukcji C++ w programie Microsoft Visual Studio C++.
ms.date: 04/15/2020
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
no-loc:
- switch
- case
- default
- break
- while
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: 1f65d4699423d74be9c75a9be47e543a9a1256e2
ms.sourcegitcommit: 9266fc76ac2e872e35a208b4249660dfdfc87cba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81480820"
---
# <a name="opno-locswitch-statement-c"></a>switchwyciąg (C++)

Umożliwia wybór między wieloma sekcjami kodu, w zależności od wartości wyrażenia integralnego.

## <a name="syntax"></a>Składnia

> **`switch (`**\[ *inicjowanie* **`;`**] *wyrażenie***`)`**\
> **`{`**\
> &nbsp;&nbsp;&nbsp;&nbsp;**`case`***constant-expression* **`:`** *instrukcja* wyrażenia stałego\
> &nbsp;&nbsp;&nbsp;&nbsp;\[**`default :`***oświadczenie*] \
> **`}`**

## <a name="remarks"></a>Uwagi

*Wyrażenie* musi mieć typ integralny lub typ klasy, który ma jednoznaczną konwersję do typu integralnego. Integralna promocja odbywa się zgodnie z opisem w [standardowych konwersjach.](standard-conversions.md)

Treść **switch** instrukcji składa się **case** z serii **default** etykiet i etykiety opcjonalnej. Zbiorczo instrukcje, które następują po etykietach są *nazywane instrukcjami etykietowanymi.* Instrukcje oznaczone etykietą nie są wymaganiami składni, ale instrukcja **switch** jest bez znaczenia bez nich. Żadne dwa wyrażenia **case** stałe w instrukcjach mogą oceniać tę samą wartość. Etykieta **default** może pojawić się tylko raz. Instrukcja **default** jest często umieszczana na końcu, ale może **switch** pojawić się w dowolnym miejscu w treści instrukcji. **case** Etykieta **default** lub etykieta **switch** może pojawić się tylko wewnątrz instrukcji.

Wyrażenie *stałe* w **case** każdej etykiecie jest konwertowane na typ *wyrażenia*. Następnie jest porównywany z *wyrażeniem* równości. Formant przekazuje do **case** instrukcji, której *wyrażenie stałe* odpowiada wartości *wyrażenia*. Wynikowe zachowanie jest pokazane w poniższej tabeli.

### <a name="switch-statement-behavior"></a>Przełączanie zachowania instrukcji

| Warunek | Akcja |
|--|--|
| Przekonwertowana wartość odpowiada wartości promowanego wyrażenia sterującego. | Formant jest przenoszony do instrukcji następującej po tej etykiecie. |
| Żadna ze stałych nie odpowiada **case** stałym w etykietach; etykieta **default** jest obecna. | Formant jest przenoszony na etykietę. **default** |
| Żadna ze stałych nie odpowiada **case** stałym w etykietach; nie **default** ma etykiety. | Kontrola jest przekazywana do **switch** instrukcji po instrukcji. |

Jeśli zostanie znalezione pasujące wyrażenie, **case** wykonanie **default** można kontynuować za pośrednictwem później lub etykiety. Instrukcja [`break`](../cpp/break-statement-cpp.md) jest używana do zatrzymania wykonywania i **switch** przenoszenia kontroli do instrukcji po instrukcji. Bez **break** instrukcji wykonywana jest każda **case** instrukcja od dopasowanej etykiety do końca **switch**, w tym **default** do . Przykład:

```cpp
// switch_statement1.cpp
#include <stdio.h>

int main() {
   const char *buffer = "Any character stream";
   int uppercase_A, lowercase_a, other;
   char c;
   uppercase_A = lowercase_a = other = 0;

   while ( c = *buffer++ )   // Walks buffer until NULL
   {
      switch ( c )
      {
         case 'A':
            uppercase_A++;
            break;
         case 'a':
            lowercase_a++;
            break;
         default:
            other++;
      }
   }
   printf_s( "\nUppercase A: %d\nLowercase a: %d\nTotal: %d\n",
      uppercase_A, lowercase_a, (uppercase_A + lowercase_a + other) );
}
```

W powyższym `uppercase_A` przykładzie jest zwiększany, jeśli `c` `'A'`jest wielką literą . Instrukcja **break** `uppercase_A++` po zakończeniu wykonywania **switch** treści instrukcji i **while** kontroli przechodzi do pętli. Bez **break** instrukcji wykonanie "przejdzie" do następnej etykiety instrukcji, `lowercase_a` `other` tak aby i również były zwiększane. Podobny cel służy oświadczeniu **break** dla `case 'a'`. Jeśli `c` jest mała `'a'`litera , `lowercase_a` jest zwiększana i instrukcja **break** kończy treść **switch** instrukcji. Jeśli `c` instrukcja `'a'` nie `'A'`jest **default** lub , jest wykonywana.

**Visual Studio 2017 i nowsze:** (dostępne z [/std:c++17](../build/reference/std-specify-language-standard-version.md)) Atrybut `[[fallthrough]]` jest określony w standardzie C++ 17. Można go użyć **switch** w instrukcji. Jest to wskazówka do kompilatora lub ktokolwiek, kto czyta kod, że zachowanie fall-through jest zamierzone. Kompilator Microsoft C++ obecnie nie ostrzega o zachowaniu fallthrough, więc ten atrybut nie ma wpływu na zachowanie kompilatora. W tym przykładzie atrybut zostanie zastosowany do pustej instrukcji w instrukcji nieokreślonej etykiety. Innymi słowy, średnik jest konieczny.

```cpp
int main()
{
    int n = 5;
    switch (n)
    {

    case 1:
        a();
        break;
    case 2:
        b();
        d();
        [[fallthrough]]; // I meant to do this!
    case 3:
        c();
        break;
    default:
        d();
        break;
    }

    return 0;
}
```

**Visual Studio 2017 w wersji 15.3 i nowszej** (dostępne z [/std:c++17](../build/reference/std-specify-language-standard-version.md)). Instrukcja switch może mieć klauzulę *inicjowania.* Wprowadza i inicjuje zmienną, której zakres jest switch ograniczony do bloku instrukcji:

```cpp
    switch (Gadget gadget(args); auto s = gadget.get_status())
    {
    case status::good:
        gadget.zip();
        break;
    case status::bad:
        throw BadGadget();
    };
```

Wewnętrzny blok **switch** instrukcji może zawierać definicje z inicjalizowania tak długo, jak są one *osiągalne*, to znaczy, nie pomijane przez wszystkie możliwe ścieżki wykonywania. Nazwy wprowadzone przy użyciu tych deklaracji mają zakres lokalny. Przykład:

```cpp
// switch_statement2.cpp
// C2360 expected
#include <iostream>
using namespace std;
int main(int argc, char *argv[])
{
    switch( tolower( *argv[1] ) )
    {
        // Error. Unreachable declaration.
        char szChEntered[] = "Character entered was: ";

    case 'a' :
        {
        // Declaration of szChEntered OK. Local scope.
        char szChEntered[] = "Character entered was: ";
        cout << szChEntered << "a\n";
        }
        break;

    case 'b' :
        // Value of szChEntered undefined.
        cout << szChEntered << "b\n";
        break;

    default:
        // Value of szChEntered undefined.
        cout << szChEntered << "neither a nor b\n";
        break;
    }
}
```

Instrukcja **switch** może być zagnieżdżona. Gdy **case** zagnieżdżone, lub **default** **switch** etykiety skojarzyć z najbliższej instrukcji, która je otacza.

### <a name="microsoft-specific-behavior"></a>Zachowanie specyficzne dla firmy Microsoft

Microsoft C nie ogranicza liczby **case** wartości **switch** w instrukcji. Liczba jest ograniczona tylko przez dostępną pamięć. ANSI C wymaga, aby **case** co najmniej 257 etykiet było dozwolonych w oświadczeniu. **switch**

Dla default microsoft c jest to, że rozszerzenia firmy Microsoft są włączone. Użyj opcji kompilatora [/Za,](../build/reference/za-ze-disable-language-extensions.md) aby wyłączyć te rozszerzenia.

## <a name="see-also"></a>Zobacz też

[Instrukcje wyboru](../cpp/selection-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
