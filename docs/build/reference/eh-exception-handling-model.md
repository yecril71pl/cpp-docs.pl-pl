---
title: /EH (Model obsługi wyjątku)
description: Przewodnik referencyjny dotyczący opcji kompilatora Microsoft C++/EH (model obsługi wyjątków) w programie Visual Studio.
ms.date: 04/14/2020
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExceptionHandling
- /eh
- VC.Project.VCCLCompilerTool.ExceptionHandling
helpviewer_keywords:
- exception handling, compiler model
- cl.exe compiler, exception handling
- EH compiler option [C++]
- -EH compiler option [C++]
- /EH compiler option [C++]
no-loc:
- ':::no-loc(SEH):::'
- ':::no-loc(try):::'
- ':::no-loc(catch):::'
- ':::no-loc(throw):::'
- ':::no-loc(extern):::'
- ':::no-loc(finally):::'
- ':::no-loc(noexcept):::'
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
ms.openlocfilehash: f158e951d595d5934ff513254871710db5920bf1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232719"
---
# <a name="eh-exception-handling-model"></a>/EH (Model obsługi wyjątku)

Określa obsługę modelu obsługi wyjątków wygenerowaną przez kompilator. Argumenty określają, czy ma zostać zastosowana `:::no-loc(catch):::(...)` składnia zarówno dla wyjątków ze strukturą, jak i standard C++, niezależnie od tego, czy kod ** :::no-loc(extern)::: "C"** jest przyjęty dla :::no-loc(throw)::: wyjątków, oraz czy należy zoptymalizować niektóre **`:::no-loc(noexcept):::`** testy.

## <a name="syntax"></a>Składnia

> **`/EHa`**[**`-`**]\
> **`/EHs`**[**`-`**]\
> **`/EHc`**[**`-`**]\
> **`/EHr`**[**`-`**]

## <a name="arguments"></a>Argumenty

**`a`**\
Włącza odwracanie standardowego stosu języka C++. Przechwytuje zarówno strukturalne (asynchroniczne), jak i standardowe wyjątki języka C++ przy użyciu `:::no-loc(catch):::(...)` składni. **`/EHa`** zastępuje oba **`/EHs`** **`/EHc`** argumenty i.

**`s`**\
Włącza odwracanie standardowego stosu języka C++. Przechwytuje tylko standardowe wyjątki C++ przy użyciu `:::no-loc(catch):::(...)` składni. O ile nie **`/EHc`** jest również określony, kompilator zakłada, że funkcje zadeklarowane jako ** :::no-loc(extern)::: "C"** mogą wystąpić :::no-loc(throw)::: wyjątek języka C++.

**`c`**\
Gdy jest używany z **`/EHs`** , kompilator zakłada, że funkcje zadeklarowane jako ** :::no-loc(extern)::: "C"** nigdy nie mają :::no-loc(throw)::: wyjątku C++. Nie ma żadnego efektu, gdy jest używany z **`/EHa`** (czyli **`/EHca`** jest równoważne z **`/EHa`** ). **`/EHc`** jest ignorowany **`/EHs`** , jeśli lub **`/EHa`** nie określono.

**`r`**\
Informuje kompilator, aby zawsze generował testy zakończenia środowiska uruchomieniowego dla wszystkich **`:::no-loc(noexcept):::`** funkcji. Domyślnie testy środowiska uruchomieniowego dla programu **`:::no-loc(noexcept):::`** mogą zostać zoptymalizowane, jeśli kompilator określi, że funkcja wywołuje tylko funkcje niebędące w :::no-loc(throw)::: toku. Ta opcja zapewnia ścisłą zgodność języka C++ według kosztu dodatkowego kodu. **`/EHr`** jest ignorowany **`/EHs`** , jeśli lub **`/EHa`** nie określono.

**`-`**\
Czyści poprzedni argument opcji. Na przykład, **`/EHsc-`** jest interpretowany jako **`/EHs /EHc-`** i jest równoważne **`/EHs`** .

**`/EH`** Argumenty mogą być określone osobno lub połączone w dowolnej kolejności. Jeśli określono więcej niż jedno wystąpienie tego samego argumentu, ostatnie zastępuje wszystkie wcześniejsze.  Na przykład **`/EHr- /EHc /EHs`** jest taka sama jak **`/EHscr-`** i ma ten **`/EHscr- /EHr`** sam skutek co **`/EHscr`** .

## <a name="remarks"></a>Uwagi

### <a name="default-exception-handling-behavior"></a>Domyślne zachowanie obsługi wyjątków

Kompilator zawsze generuje kod, który obsługuje asynchroniczne obsłudze wyjątków ( :::no-loc(SEH)::: ). Domyślnie, jeśli nie, **`/EHsc`** **`/EHs`** lub **`/EHa`** opcja jest określona, kompilator obsługuje :::no-loc(SEH)::: procedury obsługi w natywnej `:::no-loc(catch):::(...)` klauzuli C++. Jednak generuje również kod, który tylko częściowo obsługuje wyjątki C++. Domyślny kod odwinięcia wyjątku nie niszczy automatycznych obiektów C++ poza [:::no-loc(try):::](../../cpp/:::no-loc(try):::-:::no-loc(throw):::-and-:::no-loc(catch):::-statements-cpp.md) blokami, które wykraczają poza zakres z powodu wyjątku. Przecieki zasobów i niezdefiniowane zachowanie mogą wynikać z wyjątku C++ :::no-loc(throw)::: .

### <a name="standard-c-exception-handling"></a>Standardowa obsługa wyjątków C++

Pełna obsługa kompilatora dla modelu obsługi wyjątków standardowego języka C++, które bezpiecznie rozwinięcia obiektów stosu, wymaga **`/EHsc`** (zalecane), **`/EHs`** lub **`/EHa`** .

Jeśli używasz **`/EHs`** lub **`/EHsc`** , `:::no-loc(catch):::(...)` klauzule nie mają :::no-loc(catch)::: asynchronicznych wyjątków strukturalnych. Wszystkie naruszenia dostępu i <xref:System.Exception?displayProperty=fullName> wyjątki zarządzane przechodzą nieprzechwycone. I obiekty w zakresie, gdy wystąpi wyjątek asynchroniczny nie są niszczone, nawet jeśli kod obsługuje wyjątek asynchroniczny. To zachowanie jest argumentem dla pozostawienia nieobsłużonych wyjątków strukturalnych. Zamiast tego należy wziąć pod uwagę te wyjątki krytyczne.

Gdy używasz **`/EHs`** lub **`/EHsc`** , kompilator zakłada, że wyjątki mogą wystąpić tylko w **`:::no-loc(throw):::`** instrukcji lub w wywołaniu funkcji. To założenie pozwala kompilatorowi wyeliminować kod służący do śledzenia okresu istnienia wielu niezmienionych obiektów, co może znacznie zmniejszyć rozmiar kodu. Jeśli używasz **`/EHa`** , obraz wykonywalny może być większy i wolniejszy, ponieważ kompilator nie optymalizuje **`:::no-loc(try):::`** bloków tak agresywnie. Pozostawia również filtry wyjątków, które automatycznie czyści obiekty lokalne, nawet jeśli kompilator nie widzi żadnego kodu, który może :::no-loc(throw)::: mieć wyjątek języka C++.

### <a name="structured-and-standard-c-exception-handling"></a>Obsługa wyjątków strukturalnych i standardowych C++

**`/EHa`** Opcja kompilatora umożliwia rozwinięcia awaryjnego stosu dla wyjątków asynchronicznych i wyjątków C++. Obsługuje ona zarówno standardowe, jak i strukturalne wyjątki, przy użyciu natywnej `:::no-loc(catch):::(...)` klauzuli c++. Aby zaimplementować :::no-loc(SEH)::: bez określenia **`/EHa`** , można użyć **__ :::no-loc(try)::: **, **`__except`** , i **`__:::no-loc(finally):::`** składni. Aby uzyskać więcej informacji, zobacz [strukturalna obsługa wyjątków](../../cpp/structured-exception-handling-c-cpp.md).

> [!IMPORTANT]
> Określenie **`/EHa`** i :::no-loc(try)::: przejściu do obsługi wszystkich wyjątków za pomocą `:::no-loc(catch):::(...)` może być niebezpieczne. W większości przypadków wyjątki asynchroniczne są nie do odzyskania i powinny być uważane za krytyczne. Ich wychwytywanie i kontynuacja wykonania aplikacji może spowodować uszkodzenie procesu i prowadzić do błędów, które trudno znaleźć i naprawić.
>
> Mimo że systemy Windows i Visual C++ obsługują :::no-loc(SEH)::: , zdecydowanie zalecamy użycie obsługi wyjątków ISO-standard C++ ( **`/EHsc`** lub **`/EHs`** ). Sprawia, że kod jest bardziej przenośny i elastyczny. Nadal może być konieczne użycie :::no-loc(SEH)::: w starszym kodzie lub dla określonych rodzajów programów. Jest to wymagane w kodzie skompilowanym do obsługi środowiska uruchomieniowego języka wspólnego ([/CLR](clr-common-language-runtime-compilation.md)), na przykład. Aby uzyskać więcej informacji, zobacz [strukturalna obsługa wyjątków](../../cpp/structured-exception-handling-c-cpp.md).
>
> Zaleca się, aby nigdy nie łączyć plików obiektów skompilowanych przy użyciu **`/EHa`** do skompilowanych za pomocą **`/EHs`** lub **`/EHsc`** w tym samym module wykonywalnym. Jeśli musisz obsłużyć wyjątek asynchroniczny przy użyciu **`/EHa`** dowolnego miejsca w module, użyj polecenia, **`/EHa`** Aby skompilować cały kod w module. Składnia obsługi wyjątków strukturalnych może być używana w tym samym module co kod, który jest kompilowany przy użyciu **`/EHs`** . Nie można jednak mieszać :::no-loc(SEH)::: składni z C++ **`:::no-loc(try):::`** , **`:::no-loc(throw):::`** i **`:::no-loc(catch):::`** w tej samej funkcji.

Użyj **`/EHa`** , jeśli chcesz :::no-loc(catch)::: , aby wyjątek, który jest wywoływany przez coś innego niż **`:::no-loc(throw):::`** . Ten przykład generuje i :::no-loc(catch)::: es wyjątek strukturalny:

```cpp
// compiler_options_EHA.cpp
// compile with: /EHa
#include <iostream>
#include <excpt.h>
using namespace std;

void fail()
{
    // generates SE and attempts to :::no-loc(catch)::: it using :::no-loc(catch):::(...)
    :::no-loc(try):::
    {
        int i = 0, j = 1;
        j /= i;   // This will :::no-loc(throw)::: a SE (divide by zero).
        printf("%d", j);
    }
    :::no-loc(catch):::(...)
    {
        // :::no-loc(catch)::: block will only be executed under /EHa
        cout << "Caught an exception in :::no-loc(catch):::(...)." << endl;
    }
}

int main()
{
    __:::no-loc(try):::
    {
        fail();
    }

    // __except will only :::no-loc(catch)::: an exception here
    __except(EXCEPTION_EXECUTE_HANDLER)
    {
        // if the exception was not caught by the :::no-loc(catch):::(...) inside fail()
        cout << "An exception was caught in __except." << endl;
    }
}
```

### <a name="exception-handling-under-clr"></a>Obsługa wyjątków w/CLR

**`/clr`** Opcja oznacza (oznacza to **`/EHa`** , że **`/clr /EHa`** jest nadmiarowa). Kompilator generuje błąd **`/EHs`** , jeśli lub **`/EHsc`** jest używany po **`/clr`** . Optymalizacje nie wpływają na to zachowanie. W przypadku przechwyconego wyjątku kompilator wywołuje destruktory klas dla wszystkich obiektów, które znajdują się w tym samym zakresie co wyjątek. Jeśli nie przechwycono wyjątku, te destruktory nie są uruchamiane.

Aby uzyskać informacje na temat ograniczeń obsługi wyjątków w programie **`/clr`** , zobacz [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md).

### <a name="runtime-exception-checks"></a>Testy wyjątków czasu wykonywania

**`/EHr`** Opcja wymusza zakończenie wykonywania przez wszystkie funkcje, które mają **`:::no-loc(noexcept):::`** atrybut. Domyślnie testy środowiska uruchomieniowego mogą być optymalizowane, jeśli zaplecze kompilatora ustali, że funkcja wywołuje tylko * :::no-loc(throw)::: funkcje nieobsługujące* . :::no-loc(throw):::Funkcje, które mają atrybut, który określa brak wyjątków, mogą być :::no-loc(throw)::: n. Obejmują one funkcje oznaczone **`:::no-loc(noexcept):::`** , `:::no-loc(throw):::()` , `__declspec(no:::no-loc(throw):::)` , i, gdy **`/EHc`** jest określony, funkcje ** :::no-loc(extern)::: "C"** . :::no-loc(throw):::Funkcje niedziałające obejmują również wszystkie te, które zostały określone przez kompilator jako niebędący :::no-loc(throw)::: w wyniku inspekcji. Można jawnie ustawić zachowanie domyślne przy użyciu **`/EHr-`** .

Atrybut nieobsługujący nie :::no-loc(throw)::: jest gwarancją, że wyjątki nie mogą być :::no-loc(throw)::: n przez funkcję. W przeciwieństwie do zachowania **`:::no-loc(noexcept):::`** funkcji, kompilator MSVC traktuje wyjątek :::no-loc(throw)::: n przez funkcję zadeklarowaną przy użyciu `:::no-loc(throw):::()` , `__declspec(no:::no-loc(throw):::)` lub ** :::no-loc(extern)::: "C"** jako niezdefiniowane zachowanie. Funkcje korzystające z tych trzech atrybutów deklaracji nie wymuszają sprawdzania zakończenia środowiska uruchomieniowego dla wyjątków. Możesz użyć **`/EHr`** opcji, aby pomóc w zidentyfikowaniu tego niezdefiniowanego zachowania, wymuszając kompilatorowi generowanie testów dla nieobsłużonych wyjątków, które ucieczką **`:::no-loc(noexcept):::`** funkcję.

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>Ustawianie opcji w programie Visual Studio lub programowo

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz pozycję **Właściwości konfiguracji**  >  generowanie kodu**C/C++**  >  **Code Generation**.

1. Zmodyfikuj właściwość **Włącz wyjątki C++** .

   Lub ustaw opcję **Włącz wyjątki C++** na wartość **nie**, a następnie na stronie właściwości **wiersza polecenia** w polu **dodatkowe opcje** Dodaj kompilator opcji.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)\
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)\
[Błędy i obsługa wyjątków](../../cpp/errors-and-exception-handling-modern-cpp.md)\
[Specyfikacje wyjątków ( :::no-loc(throw)::: )](../../cpp/exception-specifications-:::no-loc(throw):::-cpp.md)\
[Obsługa wyjątków strukturalnych (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)
