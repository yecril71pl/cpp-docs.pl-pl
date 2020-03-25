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
ms.openlocfilehash: 6b09c0eac939f7ca6a12b68ce5deb3fb83ad27c6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160817"
---
# <a name="switch-statement-c"></a>switch — instrukcja (C++)

Zezwala na wybór między wieloma sekcjami kodu, w zależności od wartości wyrażenia całkowitego.

## <a name="syntax"></a>Składnia

```
   switch ( init; expression )
   case constant-expression : statement
   [default  : statement]
```

## <a name="remarks"></a>Uwagi

*Wyrażenie* musi być typem całkowitym lub typem klasy, dla którego istnieje jednoznaczna konwersja na typ całkowity. Promocja typu całkowitego jest wykonywana zgodnie z opisem w temacie [Konwersje standardowe](standard-conversions.md).

Treść instrukcji **Switch** składa się z serii etykiet **wielkości liter** i opcjonalnej etykiety **domyślnej** . W instrukcjach **Case** nie mogą być obliczane dwa wyrażenia stałe o tej samej wartości. Etykieta **Domyślna** może wystąpić tylko raz. Instrukcje etykietowane nie są wymaganiami składni, ale instrukcja **Switch** nie ma znaczenia.   Instrukcja domyślna nie musi znajdować się na końcu; może pojawić się w dowolnym miejscu w treści instrukcji switch. Etykieta Case lub default może wystąpić tylko wewnątrz instrukcji switch.

*Wyrażenie stałe* w każdej etykiecie **Case** jest konwertowane na typ *wyrażenia* i porównywane z *wyrażeniem* dla równości. Kontrolka przechodzi do instrukcji, której **wielkość liter** *— wyrażenie* dopasowuje wartość *wyrażenia*. Wynikowe zachowanie jest pokazane w poniższej tabeli.

### <a name="switch-statement-behavior"></a>Zachowanie instrukcji switch

|Warunek|Akcja|
|---------------|------------|
|Przekonwertowana wartość jest zgodna z wyróżnionym wyrażeniem kontroli.|Kontrolka jest przenoszona do instrukcji następującej po etykiecie.|
|Żadna ze stałych nie pasuje do stałych w etykietach **przypadku** ; obecna jest etykieta **Domyślna** .|Kontrolka jest przenoszona do etykiety **domyślnej** .|
|Żadna ze stałych nie pasuje do stałych w etykietach **przypadku** ; Etykieta **Domyślna** nie jest obecna.|Kontrolka jest przekazywana do instrukcji po instrukcji **Switch** .|

Jeśli zostanie znalezione pasujące wyrażenie, kontrolka nie jest obsługiwana w kolejnych etykietach instrukcji **Case** i **default** . Instrukcja [Break](../cpp/break-statement-cpp.md) jest używana, aby zatrzymać wykonywanie i transfer kontroli do instrukcji po instrukcji **Switch** . Bez instrukcji **Break** , jest wykonywana każda instrukcja z dopasowanej etykiety **Case** do końca **przełącznika**, łącznie z **wartością domyślną**. Na przykład:

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

W powyższym przykładzie `capa` jest zwiększana, jeśli `c` jest `A`wielką literą. Instrukcja **Break** po `capa++` kończy wykonywanie treści instrukcji **Switch** i kontrola przechodzi do pętli **while** . Bez instrukcji **Break** wykonanie "przepada" do następnej instrukcji oznaczonej etykietą, tak aby `lettera` i `nota` również były zwiększane. Podobny cel jest obsługiwany przez instrukcję **Break** dla `case 'a'`. Jeśli `c` jest małymi literami `a`, `lettera` jest zwiększana, a instrukcja **Break** kończy treść instrukcji **Switch** . Jeśli `c` nie jest `a` lub `A`, zostanie wykonana instrukcja **Domyślna** .

**Visual Studio 2017 i nowsze:** (dostępne w [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)) atrybut `[[fallthrough]]` jest określony w standardzie c++ 17. Może być używana w instrukcji **Switch** jako Wskazówka do kompilatora (lub do każdego odczytu kodu), że jest zamierzone zachowanie. Kompilator firmy C++ Microsoft obecnie nie ostrzega w przypadku zachowania fallthrough, więc ten atrybut nie ma wpływu na zachowanie kompilatora. Należy zauważyć, że atrybut jest stosowany do pustej instrukcji w instrukcji oznaczonej etykietą. Innymi słowy, średnik jest zbędny.

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

**Visual Studio 2017 w wersji 15,3 lub nowszej** (dostępny w [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): instrukcja SWITCH może wprowadzić i zainicjować zmienną, której zakres jest ograniczony do bloku instrukcji switch:

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

Wewnętrzny blok instrukcji **Switch** może zawierać definicje z inicjalizacjami o ile są one osiągalne — to znaczy, które nie są pomijane przez wszystkie możliwe ścieżki wykonywania. Nazwy wprowadzone przy użyciu tych deklaracji mają zakres lokalny. Na przykład:

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

Instrukcja **Switch** może być zagnieżdżona. W takich przypadkach etykiety **Case** lub **default** są skojarzone z najbliższą instrukcją **Switch** , która je obejmuje.

**Specyficzne dla firmy Microsoft**

Firma Microsoft C nie ogranicza liczby wartości wielkości liter w instrukcji **Switch** . Liczba jest ograniczona tylko przez dostępną pamięć. ANSI C wymaga co najmniej 257 etykiet wielkości liter w instrukcji **Switch** .

Domyślnym ustawieniem dla Microsoft C jest włączenie rozszerzeń Microsoft. Aby wyłączyć te rozszerzenia, użyj opcji kompilatora [/za](../build/reference/za-ze-disable-language-extensions.md) .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Instrukcje wyboru](../cpp/selection-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
