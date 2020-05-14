---
title: switchInstrukcja (C++)
description: Odwołanie do standardowej instrukcji C++ switch w Microsoft Visual Studio C++.
ms.date: 04/25/2020
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
- opt
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: d43a7a64b5a74f00833093ae8999d73edd7f5753
ms.sourcegitcommit: c4cf8976939dd0e13e25b82930221323ba6f15d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83389704"
---
# <a name="switch-statement-c"></a>`switch`Instrukcja (C++)

Zezwala na wybór między wieloma sekcjami kodu, w zależności od wartości wyrażenia całkowitego.

## <a name="syntax"></a>Składnia

> *`selection-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp;__`switch`__&nbsp;__`(`__&nbsp;*`init-statement`*<sub>opt</sub> <sup>C++ 17</sup>&nbsp;*`condition`*&nbsp;__`)`__&nbsp;*`statement`*

> *`init-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression-statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`simple-declaration`*

> *`condition`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`attribute-specifier-seq`*<sub>opt</sub>&nbsp;*`decl-specifier-seq`*&nbsp;*`declarator`*&nbsp;*`brace-or-equal-initializer`*

> *`labeled-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; __`case`__&nbsp;*`constant-expression`*&nbsp;__`:`__&nbsp;*`statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; __`default`__&nbsp;__`:`__&nbsp;*`statement`*

## <a name="remarks"></a>Uwagi

__`switch`__ Instrukcja powoduje, że kontrolka jest przekazywana do jednego *`labeled-statement`* w jego treści instrukcji, w zależności od wartości *`condition`* .

Typ *`condition`* musi być typem całkowitym lub być typem klasy, który ma niejednoznaczną konwersję na typ całkowity. Promocja całkowa odbywa się zgodnie z opisem w temacie [Konwersje standardowe](standard-conversions.md).

__`switch`__ Treść instrukcji składa się z serii __`case`__ etykiet i opcjonalnej __`default`__ etykiety. A *`labeled-statement`* to jedna z tych etykiet i instrukcji, które obserwują. Instrukcje oznaczone etykietami nie są wymaganiami dotyczącymi składni, ale __`switch`__ instrukcja nie ma znaczenia. *`constant-expression`* W __`case`__ instrukcjach nie mogą być oceniane dwie wartości o tej samej wartości. __`default`__ Etykieta może wystąpić tylko raz. __`default`__ Instrukcja jest często umieszczana na końcu, ale może występować w dowolnym miejscu w __`switch`__ treści instrukcji. __`case`__ Etykieta lub __`default`__ może wystąpić tylko wewnątrz __`switch`__ instrukcji.

*`constant-expression`* W każdej __`case`__ etykiecie jest konwertowana na wartość stałą, która jest tego samego typu co *`condition`* . Następnie jest porównywany ze *`condition`* względu na równość. Kontrolka przechodzi do pierwszej instrukcji po __`case`__ *`constant-expression`* wartości, która pasuje do wartości *`condition`* . Wynikowe zachowanie jest pokazane w poniższej tabeli.

### <a name="switch-statement-behavior"></a>`switch`zachowanie instrukcji

| Warunek | Akcja |
|--|--|
| Przekonwertowana wartość jest zgodna z wyróżnionym wyrażeniem kontroli. | Kontrolka jest przenoszona do instrukcji następującej po etykiecie. |
| Żadna ze stałych nie pasuje do stałych w __`case`__ etykietach; __`default`__ etykieta jest obecna. | Kontrolka jest przenoszona do __`default`__ etykiety. |
| Żadna ze stałych nie pasuje do stałych w __`case`__ etykietach; __`default`__ etykieta nie jest obecna. | Kontrolka jest przenoszona do instrukcji po __`switch`__ instrukcji. |

Jeśli zostanie znalezione pasujące wyrażenie, wykonanie może być kontynuowane przez późniejsze __`case`__ lub __`default`__ etykiety. [`break`](../cpp/break-statement-cpp.md)Instrukcja jest używana, aby zatrzymać wykonywanie i transfer kontroli do instrukcji po __`switch`__ instrukcji. Bez __`break`__ instrukcji, każda instrukcja z dopasowanej __`case`__ etykiety na końcu __`switch`__ , łącznie z __`default`__ , jest wykonywana. Przykład:

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

W powyższym przykładzie `uppercase_A` jest zwiększana, jeśli `c` jest wielką literą `'A'` . __`break`__ Instrukcja po `uppercase_A++` zakończeniu wykonywania __`switch`__ treści instrukcji i kontroli przebiega do __`while`__ pętli. Bez __`break`__ instrukcji wykonywanie "przechodzenie" do następnej instrukcji oznaczonej etykietą, tak aby `lowercase_a` i `other` również było zwiększane. Podobny cel jest obsługiwany przez __`break`__ instrukcję dla `case 'a'` . Jeśli `c` jest małymi literami `'a'` , `lowercase_a` jest zwiększana, a __`break`__ instrukcja kończy __`switch`__ treść instrukcji. Jeśli `c` nie jest `'a'` lub `'A'` , __`default`__ instrukcja jest wykonywana.

**Visual Studio 2017 i nowsze:** (dostępne w [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)) `[[fallthrough]]` atrybut jest określony w standardzie c++ 17. Można go użyć w __`switch`__ instrukcji. Jest to Wskazówka dla kompilatora lub każda osoba, która odczytuje kod, że działanie wykraczające jest zamierzone. Kompilator języka Microsoft C++ aktualnie nie ostrzega o zachowania fallthrough, więc ten atrybut nie ma wpływu na zachowanie kompilatora. W tym przykładzie atrybut jest stosowany do pustej instrukcji w niezakończonej instrukcji oznaczonej etykietą. Innymi słowy, średnik jest niezbędny.

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

**Visual Studio 2017 w wersji 15,3 lub nowszej** (dostępny w [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)). __`switch`__ Instrukcja może zawierać *`init-statement`* klauzulę kończącą się średnikiem. Wprowadza i inicjuje zmienną, której zakres jest ograniczony do bloku __`switch`__ instrukcji:

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

Wewnętrzny blok __`switch`__ instrukcji może zawierać definicje z inicjatorami o ile są one *osiągalne*, czyli nie są pomijane przez wszystkie możliwe ścieżki wykonywania. Nazwy wprowadzone przy użyciu tych deklaracji mają zakres lokalny. Przykład:

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

__`switch`__ Instrukcja może być zagnieżdżona. Gdy jest zagnieżdżony __`case`__ , __`default`__ etykiety lub są kojarzone z najbliższą __`switch`__ instrukcją, która je obejmuje.

### <a name="microsoft-specific-behavior"></a>Zachowanie specyficzne dla firmy Microsoft

Program Microsoft C++ nie ogranicza liczby __`case`__ wartości w __`switch`__ instrukcji. Liczba jest ograniczona tylko przez dostępną pamięć.

## <a name="see-also"></a>Zobacz także

[Instrukcje wyboru](../cpp/selection-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
