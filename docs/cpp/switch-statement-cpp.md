---
title: switch — instrukcja (C++)
ms.date: 05/06/2019
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: 8136b03d9e54b4d49bcb1417238066bd86bc6b89
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221938"
---
# <a name="switch-statement-c"></a>switch — instrukcja (C++)

Umożliwia wybór między wielokrotnymi sekcjami kodu, w zależności od wartości wyrażenia liczby całkowitej.

## <a name="syntax"></a>Składnia

```
   switch ( init; expression )
   case constant-expression : statement
   [default  : statement]
```

## <a name="remarks"></a>Uwagi

*Wyrażenie* musi być typu całkowitego lub typu klasy, dla którego istnieje jednoznaczna konwersja na typ całkowitoliczbowy. Promocja typu całkowitego odbywa się zgodnie z opisem w [konwersje standardowe](standard-conversions.md).

**Przełącz** treść instrukcji składa się z szeregu **przypadek** etykiet i opcjonalnej **domyślne** etykiety. Żadne dwa wyrażenia stałe w **przypadek** instrukcji można ocenić tę samą wartość. **Domyślne** etykieta może wystąpić tylko raz. Instrukcje opatrzone etykietami nie są wymaganiami składni, ale **Przełącz** instrukcja jest bez znaczenia bez nich.   Domyślna deklaracja nie musi pojawić się na końcu; go może występować w dowolnym miejscu w treści instrukcji switch. Sprawa lub domyślna etykieta może wystąpić tylko wewnątrz instrukcji switch.

*Wyrażenie_stałe* w każdym **przypadek** etykiety jest konwertowane na typ *wyrażenie* i w porównaniu z *wyrażenie* dla równości. Kontrola przechodzi do instrukcji, których **przypadek** *wyrażenie_stałe* odpowiada wartości *wyrażenie*. Zachowanie wynikowe jest przedstawione w poniższej tabeli.

### <a name="switch-statement-behavior"></a>Zachowanie instrukcji przełączania

|Warunek|Akcja|
|---------------|------------|
|Przekonwertowane wartości zgodne z promowanym wyrażeniem kontrolowania.|Kontrola jest przekazywana do instrukcji następującej po tej etykiecie.|
|Żadna ze stałych nie pasuje do stałych w **przypadek** etykiet; **domyślne** etykiety jest obecny.|Kontrola jest przekazywana do **domyślne** etykiety.|
|Żadna ze stałych nie pasuje do stałych w **przypadek** etykiet; **domyślne** etykieta nie jest obecny.|Kontrola jest przekazywana do instrukcji następującej po **Przełącz** instrukcji.|

Jeśli zostanie znalezione pasujące wyrażenie, formant nie jest utrudniane przez kolejne **przypadek** lub **domyślne** etykiety. [Podziału](../cpp/break-statement-cpp.md) instrukcja jest używane, aby zatrzymać wykonywanie, a kontrola jest przekazywana do instrukcji następującej po **Przełącz** instrukcji. Bez **podziału** instrukcji, każda instrukcja z dopasowanej **przypadek** etykiet na końcu **Przełącz**, w tym **domyślne**, jest wykonany. Na przykład:

```cpp
// switch_statement1.cpp
#include <stdio.h>

int main() {
   char *buffer = "Any character stream";
   int capa, lettera, nota;
   char c;
   capa = lettera = nota = 0;

   while ( c = *buffer++ )   // Walks buffer until NULL
   {
      switch ( c )
      {
         case 'A':
            capa++;
            break;
         case 'a':
            lettera++;
            break;
         default:
            nota++;
      }
   }
   printf_s( "\nUppercase a: %d\nLowercase a: %d\nTotal: %d\n",
      capa, lettera, (capa + lettera + nota) );
}
```

W powyższym przykładzie `capa` jest zwiększana, gdy `c` jest wielką `A`. **Podziału** instrukcji znajdującej się po `capa++` kończy wykonywanie **Przełącz** treści instrukcji i przekazuje kontrolę **podczas** pętli. Bez **podziału** instrukcji, wykonanie "spadnie za pośrednictwem" do następnej instrukcji etykietą, tak aby `lettera` i `nota` również by wzrosła. Podobny cel jest obsługiwany przez **podziału** poufności informacji dotyczące `case 'a'`. Jeśli `c` jest małymi literami `a`, `lettera` jest zwiększany i **podziału** kończy się **Przełącz** treść instrukcji. Jeśli `c` nie `a` lub `A`, **domyślne** instrukcja jest wykonywana.

**Visual Studio 2017 i nowszym:** (udostępniono [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md)) `[[fallthrough]]` atrybut jest określony w standardzie C ++ 17. Mogą być używane w **Przełącz** instrukcji jako wskazówka do kompilatora (lub kto czyta kodu) jest przeznaczona należą do tego zachowania. Microsoft C++ kompilatora aktualnie nie ostrzegaj przed witrynami dla fallthrough zachowania, więc ten atrybut nie ma wpływu na zachowanie kompilatora. Należy pamiętać, że atrybut jest stosowany do pustą instrukcję w ramach instrukcja labeled; innymi słowy średnik jest konieczne.

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

**Visual Studio 2017 w wersji 15.3 lub nowszej** (udostępniono [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md)):  Instrukcja switch mogą wprowadzać i Inicjowanie zmiennej, których zakres jest ograniczony do bloku instrukcji switch:

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

Wewnętrzny blok **Przełącz** instrukcji może zawierać definicje z inicjalizacji, tak długo, jak są one dostępne — to znaczy nie są pomijane przez wszystkie możliwe wykonania ścieżki. Nazwy wprowadzone za pomocą tych deklaracji mają zakres lokalny. Na przykład:

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

A **Przełącz** poufności informacji mogą być zagnieżdżone. W takich przypadkach **przypadek** lub **domyślne** etykiety są skojarzone z najbliższą **Przełącz** instrukcji, która je otacza.

**Microsoft Specific**

Microsoft C nie ogranicza liczby przypadków wartości w **Przełącz** instrukcji. Liczba jest ograniczona jedynie ilością dostępnej pamięci. ANSI C wymaga co najmniej 257 etykiet wielkości liter jest dozwolone w **Przełącz** instrukcji.

Wartość domyślna Microsoft C to, że są włączone rozszerzenia Microsoft. Użyj [/Za](../build/reference/za-ze-disable-language-extensions.md) opcję kompilatora, aby wyłączyć te rozszerzenia.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Instrukcje wyboru](../cpp/selection-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)