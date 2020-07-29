---
title: :::no-loc(switch):::Instrukcja (C++)
description: 'Odwołanie do standardowej instrukcji C++ :::no-loc(switch)::: w Microsoft Visual Studio C++.'
ms.date: 04/25/2020
f1_keywords:
- :::no-loc(default):::_cpp
- :::no-loc(switch):::_cpp
- :::no-loc(case):::_cpp
helpviewer_keywords:
- ':::no-loc(switch)::: keyword [C++]'
- ':::no-loc(case)::: keyword [C++], in :::no-loc(switch)::: statements'
- ':::no-loc(default)::: keyword [C++]'
no-loc:
- ':::no-loc(switch):::'
- ':::no-loc(case):::'
- ':::no-loc(default):::'
- ':::no-loc(break):::'
- ':::no-loc(while):::'
- ':::no-loc(opt):::'
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: d71989b6d8af0213c4cd6d4fbd8d5a84b318701a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223593"
---
# <a name="no-locswitch-statement-c"></a>`:::no-loc(switch):::`Instrukcja (C++)

Zezwala na wybór między wieloma sekcjami kodu, w zależności od wartości wyrażenia całkowitego.

## <a name="syntax"></a>Składnia

> *`selection-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp;**`:::no-loc(switch):::`**&nbsp;**`(`**&nbsp;*`init-statement`*<sub>:::no-loc(opt):::</sub> <sup>C++ 17</sup>&nbsp;*`condition`*&nbsp;**`)`**&nbsp;*`statement`*

> *`init-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression-statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`simple-declaration`*

> *`condition`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`attribute-specifier-seq`*<sub>:::no-loc(opt):::</sub>&nbsp;*`decl-specifier-seq`*&nbsp;*`declarator`*&nbsp;*`brace-or-equal-initializer`*

> *`labeled-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(case):::`**&nbsp;*`constant-expression`*&nbsp;**`:`**&nbsp;*`statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(default):::`**&nbsp;**`:`**&nbsp;*`statement`*

## <a name="remarks"></a>Uwagi

**`:::no-loc(switch):::`** Instrukcja powoduje, że kontrolka jest przekazywana do jednego *`labeled-statement`* w jego treści instrukcji, w zależności od wartości *`condition`* .

Typ *`condition`* musi być typem całkowitym lub być typem klasy, który ma niejednoznaczną konwersję na typ całkowity. Promocja całkowa odbywa się zgodnie z opisem w temacie [Konwersje standardowe](standard-conversions.md).

**`:::no-loc(switch):::`** Treść instrukcji składa się z serii **`:::no-loc(case):::`** etykiet i :::no-loc(opt)::: **`:::no-loc(default):::`** etykiety Ional. A *`labeled-statement`* to jedna z tych etykiet i instrukcji, które obserwują. Instrukcje oznaczone etykietami nie są wymaganiami dotyczącymi składni, ale **`:::no-loc(switch):::`** instrukcja nie ma znaczenia. *`constant-expression`* W **`:::no-loc(case):::`** instrukcjach nie mogą być oceniane dwie wartości o tej samej wartości. **`:::no-loc(default):::`** Etykieta może wystąpić tylko raz. **`:::no-loc(default):::`** Instrukcja jest często umieszczana na końcu, ale może występować w dowolnym miejscu w **`:::no-loc(switch):::`** treści instrukcji. **`:::no-loc(case):::`** Etykieta lub **`:::no-loc(default):::`** może wystąpić tylko wewnątrz **`:::no-loc(switch):::`** instrukcji.

*`constant-expression`* W każdej **`:::no-loc(case):::`** etykiecie jest konwertowana na wartość stałą, która jest tego samego typu co *`condition`* . Następnie jest porównywany ze *`condition`* względu na równość. Kontrolka przechodzi do pierwszej instrukcji po **`:::no-loc(case):::`** *`constant-expression`* wartości, która pasuje do wartości *`condition`* . Wynikowe zachowanie jest pokazane w poniższej tabeli.

### <a name="no-locswitch-statement-behavior"></a>`:::no-loc(switch):::`zachowanie instrukcji

| Warunek | Akcja |
|--|--|
| Przekonwertowana wartość jest zgodna z wyróżnionym wyrażeniem kontroli. | Kontrolka jest przenoszona do instrukcji następującej po etykiecie. |
| Żadna ze stałych nie pasuje do stałych w **`:::no-loc(case):::`** etykietach; **`:::no-loc(default):::`** etykieta jest obecna. | Kontrolka jest przenoszona do **`:::no-loc(default):::`** etykiety. |
| Żadna ze stałych nie pasuje do stałych w **`:::no-loc(case):::`** etykietach; **`:::no-loc(default):::`** etykieta nie jest obecna. | Kontrolka jest przenoszona do instrukcji po **`:::no-loc(switch):::`** instrukcji. |

Jeśli zostanie znalezione pasujące wyrażenie, wykonanie może być kontynuowane przez późniejsze **`:::no-loc(case):::`** lub **`:::no-loc(default):::`** etykiety. [`:::no-loc(break):::`](../cpp/:::no-loc(break):::-statement-cpp.md)Instrukcja jest używana, aby zatrzymać wykonywanie i transfer kontroli do instrukcji po **`:::no-loc(switch):::`** instrukcji. Bez **`:::no-loc(break):::`** instrukcji, każda instrukcja z dopasowanej **`:::no-loc(case):::`** etykiety na końcu **`:::no-loc(switch):::`** , łącznie z **`:::no-loc(default):::`** , jest wykonywana. Na przykład:

```cpp
// :::no-loc(switch):::_statement1.cpp
#include <stdio.h>

int main() {
   const char *buffer = "Any character stream";
   int upper:::no-loc(case):::_A, lower:::no-loc(case):::_a, other;
   char c;
   upper:::no-loc(case):::_A = lower:::no-loc(case):::_a = other = 0;

   :::no-loc(while)::: ( c = *buffer++ )   // Walks buffer until NULL
   {
      :::no-loc(switch)::: ( c )
      {
         :::no-loc(case)::: 'A':
            upper:::no-loc(case):::_A++;
            :::no-loc(break):::;
         :::no-loc(case)::: 'a':
            lower:::no-loc(case):::_a++;
            :::no-loc(break):::;
         :::no-loc(default)::::
            other++;
      }
   }
   printf_s( "\nUpper:::no-loc(case)::: A: %d\nLower:::no-loc(case)::: a: %d\nTotal: %d\n",
      upper:::no-loc(case):::_A, lower:::no-loc(case):::_a, (upper:::no-loc(case):::_A + lower:::no-loc(case):::_a + other) );
}
```

W powyższym przykładzie `upper:::no-loc(case):::_A` jest zwiększana, jeśli `c` jest górny :::no-loc(case)::: `'A'` . **`:::no-loc(break):::`** Instrukcja po `upper:::no-loc(case):::_A++` zakończeniu wykonywania **`:::no-loc(switch):::`** treści instrukcji i kontroli przebiega do **`:::no-loc(while):::`** pętli. Bez **`:::no-loc(break):::`** instrukcji wykonywanie "przechodzenie" do następnej instrukcji oznaczonej etykietą, tak aby `lower:::no-loc(case):::_a` i `other` również było zwiększane. Podobny cel jest obsługiwany przez **`:::no-loc(break):::`** instrukcję dla `:::no-loc(case)::: 'a'` . Jeśli `c` jest niższy :::no-loc(case)::: `'a'` , `lower:::no-loc(case):::_a` jest zwiększany, a **`:::no-loc(break):::`** instrukcja kończy **`:::no-loc(switch):::`** treść instrukcji. Jeśli `c` nie jest `'a'` lub `'A'` , **`:::no-loc(default):::`** instrukcja jest wykonywana.

**Visual Studio 2017 i nowsze:** (dostępne w [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)) `[[fallthrough]]` atrybut jest określony w standardzie c++ 17. Można go użyć w **`:::no-loc(switch):::`** instrukcji. Jest to Wskazówka dla kompilatora lub każda osoba, która odczytuje kod, że działanie wykraczające jest zamierzone. Kompilator języka Microsoft C++ aktualnie nie ostrzega o zachowania fallthrough, więc ten atrybut nie ma wpływu na zachowanie kompilatora. W tym przykładzie atrybut jest stosowany do pustej instrukcji w niezakończonej instrukcji oznaczonej etykietą. Innymi słowy, średnik jest niezbędny.

```cpp
int main()
{
    int n = 5;
    :::no-loc(switch)::: (n)
    {

    :::no-loc(case)::: 1:
        a();
        :::no-loc(break):::;
    :::no-loc(case)::: 2:
        b();
        d();
        [[fallthrough]]; // I meant to do this!
    :::no-loc(case)::: 3:
        c();
        :::no-loc(break):::;
    :::no-loc(default)::::
        d();
        :::no-loc(break):::;
    }

    return 0;
}
```

**Visual Studio 2017 w wersji 15,3 lub nowszej** (dostępny w [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)). **`:::no-loc(switch):::`** Instrukcja może zawierać *`init-statement`* klauzulę kończącą się średnikiem. Wprowadza i inicjuje zmienną, której zakres jest ograniczony do bloku **`:::no-loc(switch):::`** instrukcji:

```cpp
    :::no-loc(switch)::: (Gadget gadget(args); auto s = gadget.get_status())
    {
    :::no-loc(case)::: status::good:
        gadget.zip();
        :::no-loc(break):::;
    :::no-loc(case)::: status::bad:
        throw BadGadget();
    };
```

Wewnętrzny blok **`:::no-loc(switch):::`** instrukcji może zawierać definicje z inicjatorami o ile są one *osiągalne*, czyli nie są pomijane przez wszystkie możliwe ścieżki wykonywania. Nazwy wprowadzone przy użyciu tych deklaracji mają zakres lokalny. Na przykład:

```cpp
// :::no-loc(switch):::_statement2.cpp
// C2360 expected
#include <iostream>
using namespace std;
int main(int argc, char *argv[])
{
    :::no-loc(switch):::( tolower( *argv[1] ) )
    {
        // Error. Unreachable declaration.
        char szChEntered[] = "Character entered was: ";

    :::no-loc(case)::: 'a' :
        {
        // Declaration of szChEntered OK. Local scope.
        char szChEntered[] = "Character entered was: ";
        cout << szChEntered << "a\n";
        }
        :::no-loc(break):::;

    :::no-loc(case)::: 'b' :
        // Value of szChEntered undefined.
        cout << szChEntered << "b\n";
        :::no-loc(break):::;

    :::no-loc(default)::::
        // Value of szChEntered undefined.
        cout << szChEntered << "neither a nor b\n";
        :::no-loc(break):::;
    }
}
```

**`:::no-loc(switch):::`** Instrukcja może być zagnieżdżona. Gdy jest zagnieżdżony **`:::no-loc(case):::`** , **`:::no-loc(default):::`** etykiety lub są kojarzone z najbliższą **`:::no-loc(switch):::`** instrukcją, która je obejmuje.

### <a name="microsoft-specific-behavior"></a>Zachowanie specyficzne dla firmy Microsoft

Program Microsoft C++ nie ogranicza liczby **`:::no-loc(case):::`** wartości w **`:::no-loc(switch):::`** instrukcji. Liczba jest ograniczona tylko przez dostępną pamięć.

## <a name="see-also"></a>Zobacz także

[Instrukcje wyboru](../cpp/selection-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
