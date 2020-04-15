---
title: Omówienie modułów w języku C++
ms.date: 12/13/2019
helpviewer_keywords:
- modules [C++]
- modules [C++], overview
description: Moduły w języku C++20 stanowią nowoczesną alternatywę dla plików nagłówkowych.
ms.openlocfilehash: cd45be1dee888c8caeb65b7ff002ac8fee1ecbe1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370757"
---
# <a name="overview-of-modules-in-c"></a>Omówienie modułów w języku C++

C++20 wprowadza *moduły*, nowoczesne rozwiązanie do componentizacji bibliotek i programów C++. Moduł to zestaw plików kodu źródłowego, które są kompilowane niezależnie od [jednostek tłumaczenia,](https://wikipedia.org/wiki/Translation_unit_(programming)) które je importują. Moduły eliminują lub znacznie zmniejszają wiele problemów związanych z użyciem plików nagłówkowych, a także potencjalnie skracają czas kompilacji. Makra, dyrektywy preprocesora i nieeksportowane nazwy zadeklarowane w module nie są widoczne i dlatego nie mają wpływu na kompilację jednostki tłumaczenia, która importuje moduł. Moduły można importować w dowolnej kolejności bez obawy o ponowne zdefiniowanie makr. Deklaracje w jednostce tłumaczenia importującego nie uczestniczą w rozpoznawaniu przeciążenia ani odnośniki nazw w importowanym module. Po raz y moduł jest kompilowany, wyniki są przechowywane w pliku binarnym, który opisuje wszystkie eksportowane typy, funkcje i szablony. Ten plik może być przetwarzany znacznie szybciej niż plik nagłówka i może być ponownie przez kompilator w każdym miejscu, w którym moduł jest importowany w projekcie.

Moduły mogą być używane obok siebie z plikami nagłówkowymi. Plik źródłowy języka C++ może importować moduły, a także #include pliki nagłówkowe. W niektórych przypadkach plik nagłówka może być importowany jako moduł, a nie tekstowo #included przez preprocesora. Zaleca się, aby nowe projekty używały modułów, a nie plików nagłówkowych w miarę możliwości. W przypadku większych istniejących projektów w ramach aktywnego rozwoju zalecamy eksperymentowanie z konwertacją starszych nagłówków na moduły, aby sprawdzić, czy otrzymujesz znaczące skrócenie czasu kompilacji.

## <a name="enable-modules-in-the-microsoft-c-compiler"></a>Włączanie modułów w kompilatorze Języka Microsoft C++

Od programu Visual Studio 2019 w wersji 16.2 moduły nie są w pełni zaimplementowane w kompilatorze Microsoft C++. Za pomocą funkcji modułów można tworzyć moduły z jedną partycją i importować moduły biblioteki standardowej dostarczane przez firmę Microsoft. Aby włączyć obsługę modułów, skompiluj z [/experimental:module](../build/reference/experimental-module.md) i [/std:c++latest](../build/reference/std-specify-language-standard-version.md). W projekcie programu Visual Studio kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratorze rozwiązań** i wybierz polecenie **Właściwości**. Ustaw**Language** > pozycję rozwijaną **Konfiguracja** na **Wszystkie konfiguracje,** a następnie wybierz polecenie Właściwości **konfiguracji Moduły** > języka**C/C++** > **Włącz język (eksperymentalne).**

Moduł i kod, który go zużywa, muszą być skompilowane przy tych samych opcjach kompilatora.

## <a name="consume-the-c-standard-library-as-modules"></a>Korzystanie z biblioteki standardowej języka C++ jako modułów

Chociaż nie jest określony przez standard C++ 20, firma Microsoft umożliwia implementację biblioteki standardowej języka C++ do zaimportowania jako moduły. Importując standardową bibliotekę języka C++ jako moduły, a nie #including ją za pośrednictwem plików nagłówkowych, można potencjalnie przyspieszyć czas kompilacji w zależności od rozmiaru projektu. Biblioteka jest składowana w następujące moduły:

- std.regex udostępnia zawartość \<> regex nagłówka
- system std.file system udostępnia \<zawartość systemu plików nagłówkowych>
- std.memory zapewnia zawartość \<pamięci nagłówka>
- std.threading \<udostępnia zawartość nagłówków> atomowej, \<condition_variable>, \<przyszłych>, \<> mutex, \<shared_mutex> i \<> wątków
- std.core zapewnia wszystko inne w standardowej bibliotece C++

Aby korzystać z tych modułów, wystarczy dodać deklarację importu do górnej części pliku kodu źródłowego. Przykład:

```cpp
import std.core;
import std.regex;
```

Aby korzystać z modułu Biblioteki standardowej firmy Microsoft, skompiluj program z [opcjami /EHsc](../build/reference/eh-exception-handling-model.md) i [/MD.](../build/reference/md-mt-ld-use-run-time-library.md)

## <a name="basic-example"></a>Przykład podstawowy

Poniższy przykład przedstawia prostą definicję modułu w pliku źródłowym o nazwie **Foo.ixx**. Rozszerzenie **.ixx** jest wymagane dla plików interfejsu modułu w programie Visual Studio. W tym przykładzie plik interfejsu zawiera definicję funkcji, a także deklarację. Jednak definicje mogą być również umieszczone w jednym lub kilku oddzielnych plików (jak pokazano w późniejszym przykładzie). Instrukcja **Foo moduł eksportu** wskazuje, że ten plik `Foo`jest podstawowym interfejsem dla modułu o nazwie . Modyfikator **eksportu** na `f()` wskazuje, że ta `Foo` funkcja będzie widoczna, gdy jest importowany przez inny program lub moduł. Należy zauważyć, że moduł `Bar`odwołuje się do obszaru nazw .

```cpp
export module Foo;

#define ANSWER 42

namespace Bar
{
   int f_internal() {
        return ANSWER;
      }

   export int f() {
      return f_internal();
   }
}
```

Plik **MyProgram.cpp** używa deklaracji **importu,** aby uzyskać dostęp `Foo`do nazwy eksportowanej przez program . Należy zauważyć, `Bar` że nazwa jest widoczna w tym miejscu, ale nie wszystkie jej członków. Należy również zauważyć, że makro `ANSWER` nie jest widoczne.

```cpp

import Foo;
import std.core;

using namespace std;

int main()
{
   cout << "The result of f() is " << Bar::f() << endl; // 42
   // int i = Bar::f_internal(); // C2039
   // int j = ANSWER; //C2065
}

```

Deklaracja importu może pojawić się tylko w zakresie globalnym.

## <a name="implementing-modules"></a>Wdrażanie modułów

Można utworzyć moduł z jednym plikiem interfejsu (.ixx), który eksportuje nazwy i zawiera implementacje wszystkich funkcji i typów. Implementacje można również umieścić w jednym lub więcej oddzielnych plikach implementacji, podobnie jak pliki .h i .cpp są używane. Słowo kluczowe **eksportu** jest używane tylko w pliku interfejsu. Plik implementacji można **zaimportować** inny moduł, ale nie można **wyeksportować** żadnych nazw. Pliki implementacji mogą być nazwane z dowolnym rozszerzeniem. Plik interfejsu i zestaw plików implementacyjnych, które go popierają, są traktowane jako specjalny rodzaj jednostki tłumaczeniowej zwanej *jednostką modułu.* Nazwa zadeklarowana w dowolnym pliku implementacji jest automatycznie widoczna we wszystkich innych plikach w tej samej jednostce modułu.

W przypadku większych modułów moduł można podzielić na wiele jednostek modułowych zwanych *partycjami*. Każda partycja składa się z pliku interfejsu wspieranego przez jeden lub więcej plików implementacji. (W wersji 16.2 programu Visual Studio 2019 partycje nie zostały jeszcze w pełni zaimplementowane).

## <a name="modules-namespaces-and-argument-dependent-lookup"></a>Moduły, przestrzenie nazw i wyszukiwanie zależne od argumentów

Reguły dla obszarów nazw w modułach są takie same jak w każdym innym kodzie. Jeśli deklaracja w obszarze nazw jest eksportowana, otaczający obszar nazw (z wyłączeniem nieeksportowanych elementów członkowskich) jest również niejawnie eksportowany. Jeśli obszar nazw jest jawnie eksportowany, wszystkie deklaracje w tej definicji obszaru nazw są eksportowane.

Podczas wykonywania odnośnego argumentu wyszukiwania dla rozdzielczości przeciążenia w jednostce translacji importującej kompilator bierze pod uwagę funkcje, które są zadeklarowane w tej samej jednostce translacji (w tym interfejsach modułu), ponieważ typ argumentów funkcji jest zdefiniowany.

### <a name="module-partitions"></a>Partycje modułu

> [!NOTE]
> Ta sekcja jest dostępna dla kompletności. Partycje nie są jeszcze implementowane w kompilatorze Języka Microsoft C++.

Moduł może być składowany na *partycje*, z których każdy składa się z pliku interfejsu i zero lub więcej plików implementacji. Partycja modułu jest podobna do modułu, z tą różnicą, że współużywa własność wszystkich deklaracji w całym module. Wszystkie nazwy eksportowane przez pliki interfejsu partycji są importowane i ponownie eksportowane przez podstawowy plik interfejsu. Nazwa partycji musi zaczynać się od nazwy modułu, po której następuje dwukropek. Deklaracje w dowolnej partycji są widoczne w całym module. Nie są potrzebne żadne specjalne środki ostrożności, aby uniknąć błędów jednej reguły (ODR). Można zadeklarować nazwę (funkcja, klasa itp.) w jednej partycji i zdefiniować ją w innej. Plik implementacji partycji zaczyna się w ten sposób:

```cpp
module Foo:part1
```

a plik interfejsu partycji zaczyna się w ten sposób:

```cpp
export module Foo:part1
```

Aby uzyskać dostęp do deklaracji w innej partycji, partycja musi ją zaimportować, ale może używać tylko nazwy partycji, a nie nazwy modułu:

```cpp
module Foo:part2;
import :part1;
```

Jednostka interfejsu podstawowego musi importować i ponownie eksportować wszystkie pliki partycji interfejsu modułu w ten sposób:

```cpp
export import :part1
export import :part2
...
```

Jednostka interfejsu podstawowego może importować pliki implementacji partycji, ale nie może ich wyeksportować, ponieważ pliki te nie mogą eksportować żadnych nazw. Dzięki temu moduł zachować szczegóły implementacji wewnętrzne do modułu.

## <a name="modules-and-header-files"></a>Moduły i pliki nagłówkowe

Pliki nagłówkowe można dołączyć do pliku `#include` źródłowego modułu, umieszczając dyrektywę przed deklaracją modułu. Pliki te są uważane za w *globalnym fragmencie modułu*. Moduł może zobaczyć tylko nazwy w *module globalnym fragmentu,* które znajdują się w nagłówkach jawnie zawiera. Fragment modułu globalnego zawiera tylko symbole, które są faktycznie używane.

```cpp
// MyModuleA.cpp

#include "customlib.h"
#include "anotherlib.h"

import std.core;
import MyModuleB;

//... rest of file
```

Tradycyjnego pliku nagłówka można użyć do określenia, które moduły są importowane:

```cpp
// MyProgram.h
import std.core;
#ifdef DEBUG_LOGGING
import std.filesystem;
#endif
```

### <a name="imported-header-files"></a>Zaimportowane pliki nagłówkowe

> [!NOTE]
> Ta sekcja ma tylko informacje. Starsze importy nie są jeszcze implementowane w kompilatorze Języka Microsoft C++.

Niektóre nagłówki są wystarczająco samodzielne, że mogą być wprowadzane przy użyciu słowa kluczowego **importu.** Główną różnicą między importowanym nagłówkiem a importowanym modułem jest to, że wszelkie definicje preprocesora w nagłówku są widoczne w programie importowania natychmiast po instrukcji importu. (Definicje preprocesora w plikach zawartych w tym nagłówku *nie* są widoczne).

```cpp
import <vector>
import "myheader.h"
```

## <a name="see-also"></a>Zobacz też

[moduł, import, eksport](import-export-module.md)
