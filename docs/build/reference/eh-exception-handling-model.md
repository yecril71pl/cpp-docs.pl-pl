---
title: /EH (Model obsługi wyjątku)
description: Przewodnik referencyjny dotyczący opcji kompilatora Microsoft C++/EH (model obsługi wyjątków) w programie Visual Studio.
ms.date: 08/25/2020
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
- SEH
- try
- catch
- throw
- extern
- finally
- noexcept
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
ms.openlocfilehash: 0d18d0f1d73b1de46b12262deecb2436c34e6176
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898390"
---
# <a name="eh-exception-handling-model"></a>`/EH` (Model obsługi wyjątków)

Określa obsługę modelu obsługi wyjątków wygenerowaną przez kompilator. Argumenty określają, czy ma zostać zastosowana `catch(...)` składnia zarówno dla wyjątków ze strukturą, jak i standard C++, niezależnie od tego, czy kod ** extern "C"** jest przyjęty dla throw wyjątków, oraz czy należy zoptymalizować niektóre **`noexcept`** testy.

## <a name="syntax"></a>Składnia

> **`/EHa`**[**`-`**]\
> **`/EHs`**[**`-`**]\
> **`/EHc`**[**`-`**]\
> **`/EHr`**[**`-`**]

## <a name="arguments"></a>Argumenty

**`a`**\
Włącza odwracanie standardowego stosu języka C++. Przechwytuje zarówno strukturalne (asynchroniczne), jak i standardowe wyjątki języka C++ przy użyciu `catch(...)` składni. **`/EHa`** zastępuje oba **`/EHs`** **`/EHc`** argumenty i.

**`s`**\
Włącza odwracanie standardowego stosu języka C++. Przechwytuje tylko standardowe wyjątki C++ przy użyciu `catch(...)` składni. O ile nie **`/EHc`** jest również określony, kompilator zakłada, że funkcje zadeklarowane jako ** extern "C"** mogą wystąpić throw wyjątek języka C++.

**`c`**\
Gdy jest używany z **`/EHs`** , kompilator zakłada, że funkcje zadeklarowane jako ** extern "C"** nigdy nie mają throw wyjątku C++. Nie ma żadnego efektu, gdy jest używany z **`/EHa`** (czyli **`/EHca`** jest równoważne z **`/EHa`** ). **`/EHc`** jest ignorowany **`/EHs`** , jeśli lub **`/EHa`** nie określono.

**`r`**\
Informuje kompilator, aby zawsze generował testy zakończenia środowiska uruchomieniowego dla wszystkich **`noexcept`** funkcji. Domyślnie testy środowiska uruchomieniowego dla programu **`noexcept`** mogą zostać zoptymalizowane, jeśli kompilator określi, że funkcja wywołuje tylko funkcje niebędące w throw toku. Ta opcja zapewnia ścisłą zgodność języka C++ według kosztu dodatkowego kodu. **`/EHr`** jest ignorowany **`/EHs`** , jeśli lub **`/EHa`** nie określono.

**`-`**\
Czyści poprzedni argument opcji. Na przykład, **`/EHsc-`** jest interpretowany jako **`/EHs /EHc-`** i jest równoważne **`/EHs`** .

**`/EH`** Argumenty mogą być określone osobno lub połączone w dowolnej kolejności. Jeśli określono więcej niż jedno wystąpienie tego samego argumentu, ostatnie zastępuje wszystkie wcześniejsze.  Na przykład **`/EHr- /EHc /EHs`** jest taka sama jak **`/EHscr-`** i ma ten **`/EHscr- /EHr`** sam skutek co **`/EHscr`** .

## <a name="remarks"></a>Uwagi

### <a name="default-exception-handling-behavior"></a>Domyślne zachowanie obsługi wyjątków

Kompilator zawsze generuje kod, który obsługuje asynchroniczne obsłudze wyjątków ( SEH ). Domyślnie, jeśli nie, **`/EHsc`** **`/EHs`** lub **`/EHa`** opcja jest określona, kompilator obsługuje SEH procedury obsługi w natywnej `catch(...)` klauzuli C++. Jednak generuje również kod, który tylko częściowo obsługuje wyjątki C++. Domyślny kod odwinięcia wyjątku nie niszczy automatycznych obiektów C++ poza [`try`](../../cpp/try-throw-and-catch-statements-cpp.md) blokami, które wykraczają poza zakres z powodu wyjątku. Przecieki zasobów i niezdefiniowane zachowanie mogą wynikać z wyjątku C++ throw .

### <a name="standard-c-exception-handling"></a>Standardowa obsługa wyjątków C++

Pełna obsługa kompilatora dla modelu obsługi wyjątków standardowego języka C++, które bezpiecznie rozwinięcia obiektów stosu, wymaga **`/EHsc`** (zalecane), **`/EHs`** lub **`/EHa`** .

Jeśli używasz **`/EHs`** lub **`/EHsc`** , `catch(...)` klauzule nie mają catch asynchronicznych wyjątków strukturalnych. Wszystkie naruszenia dostępu i <xref:System.Exception?displayProperty=fullName> wyjątki zarządzane przechodzą nieprzechwycone. I obiekty w zakresie, gdy wystąpi wyjątek asynchroniczny nie są niszczone, nawet jeśli kod obsługuje wyjątek asynchroniczny. To zachowanie jest argumentem dla pozostawienia nieobsłużonych wyjątków strukturalnych. Zamiast tego należy wziąć pod uwagę te wyjątki krytyczne.

Gdy używasz **`/EHs`** lub **`/EHsc`** , kompilator zakłada, że wyjątki mogą wystąpić tylko w **`throw`** instrukcji lub w wywołaniu funkcji. To założenie pozwala kompilatorowi wyeliminować kod służący do śledzenia okresu istnienia wielu niezmienionych obiektów, co może znacznie zmniejszyć rozmiar kodu. Jeśli używasz **`/EHa`** , obraz wykonywalny może być większy i wolniejszy, ponieważ kompilator nie optymalizuje **`try`** bloków tak agresywnie. Pozostawia również filtry wyjątków, które automatycznie czyści obiekty lokalne, nawet jeśli kompilator nie widzi żadnego kodu, który może throw mieć wyjątek języka C++.

### <a name="structured-and-standard-c-exception-handling"></a>Obsługa wyjątków strukturalnych i standardowych C++

**`/EHa`** Opcja kompilatora umożliwia rozwinięcia awaryjnego stosu dla wyjątków asynchronicznych i wyjątków C++. Obsługuje ona zarówno standardowe, jak i strukturalne wyjątki, przy użyciu natywnej `catch(...)` klauzuli c++. Aby zaimplementować SEH bez określenia **`/EHa`** , można użyć **`__try`** **`__except`** składni, i **`__finally`** . Aby uzyskać więcej informacji, zobacz [strukturalna obsługa wyjątków](../../cpp/structured-exception-handling-c-cpp.md).

> [!IMPORTANT]
> Określenie **`/EHa`** i try przejściu do obsługi wszystkich wyjątków za pomocą `catch(...)` może być niebezpieczne. W większości przypadków wyjątki asynchroniczne są nie do odzyskania i powinny być uważane za krytyczne. Ich wychwytywanie i kontynuacja wykonania aplikacji może spowodować uszkodzenie procesu i prowadzić do błędów, które trudno znaleźć i naprawić.
>
> Mimo że systemy Windows i Visual C++ obsługują SEH , zdecydowanie zalecamy użycie obsługi wyjątków ISO-standard C++ ( **`/EHsc`** lub **`/EHs`** ). Sprawia, że kod jest bardziej przenośny i elastyczny. Nadal może być konieczne użycie SEH w starszym kodzie lub dla określonych rodzajów programów. Jest to wymagane w kodzie skompilowanym do obsługi środowiska uruchomieniowego języka wspólnego ( [`/clr`](clr-common-language-runtime-compilation.md) ), na przykład. Aby uzyskać więcej informacji, zobacz [strukturalna obsługa wyjątków](../../cpp/structured-exception-handling-c-cpp.md).
>
> Zaleca się, aby nigdy nie łączyć plików obiektów skompilowanych przy użyciu **`/EHa`** do skompilowanych za pomocą **`/EHs`** lub **`/EHsc`** w tym samym module wykonywalnym. Jeśli musisz obsłużyć wyjątek asynchroniczny przy użyciu **`/EHa`** dowolnego miejsca w module, użyj polecenia, **`/EHa`** Aby skompilować cały kod w module. Składnia obsługi wyjątków strukturalnych może być używana w tym samym module co kod, który jest kompilowany przy użyciu **`/EHs`** . Nie można jednak mieszać SEH składni z C++ **`try`** , **`throw`** i **`catch`** w tej samej funkcji.

Użyj **`/EHa`** , jeśli chcesz catch , aby wyjątek, który jest wywoływany przez coś innego niż **`throw`** . Ten przykład generuje i catch es wyjątek strukturalny:

```cpp
// compiler_options_EHA.cpp
// compile with: /EHa
#include <iostream>
#include <excpt.h>
using namespace std;

void fail()
{
    // generates SE and attempts to catch it using catch(...)
    try
    {
        int i = 0, j = 1;
        j /= i;   // This will throw a SE (divide by zero).
        printf("%d", j);
    }
    catch(...)
    {
        // catch block will only be executed under /EHa
        cout << "Caught an exception in catch(...)." << endl;
    }
}

int main()
{
    __try
    {
        fail();
    }

    // __except will only catch an exception here
    __except(EXCEPTION_EXECUTE_HANDLER)
    {
        // if the exception was not caught by the catch(...) inside fail()
        cout << "An exception was caught in __except." << endl;
    }
}
```

### <a name="exception-handling-under-clr"></a>Obsługa wyjątków w/CLR

**`/clr`** Opcja oznacza (oznacza to **`/EHa`** , że **`/clr /EHa`** jest nadmiarowa). Kompilator generuje błąd **`/EHs`** , jeśli lub **`/EHsc`** jest używany po **`/clr`** . Optymalizacje nie wpływają na to zachowanie. W przypadku przechwyconego wyjątku kompilator wywołuje destruktory klas dla wszystkich obiektów, które znajdują się w tym samym zakresie co wyjątek. Jeśli nie przechwycono wyjątku, te destruktory nie są uruchamiane.

Aby uzyskać informacje na temat ograniczeń obsługi wyjątków w programie **`/clr`** , zobacz [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md).

### <a name="runtime-exception-checks"></a>Testy wyjątków czasu wykonywania

**`/EHr`** Opcja wymusza zakończenie wykonywania przez wszystkie funkcje, które mają **`noexcept`** atrybut. Domyślnie testy środowiska uruchomieniowego mogą być optymalizowane, jeśli zaplecze kompilatora ustali, że funkcja wywołuje tylko * throw funkcje nieobsługujące* . throwFunkcje, które mają atrybut, który określa brak wyjątków, mogą być throw n. Obejmują one funkcje oznaczone **`noexcept`** , `throw()` , `__declspec(nothrow)` , i, gdy **`/EHc`** jest określony, **`extern "C"`** Functions. throwFunkcje niedziałające obejmują również wszystkie te, które zostały określone przez kompilator jako niebędący throw w wyniku inspekcji. Można jawnie ustawić zachowanie domyślne przy użyciu **`/EHr-`** .

Atrybut nieobsługujący nie throw jest gwarancją, że wyjątki nie mogą być throw n przez funkcję. W przeciwieństwie do zachowania **`noexcept`** funkcji, KOMPILATOR MSVC traktuje wyjątek throw n przez funkcję zadeklarowaną przy użyciu `throw()` , `__declspec(nothrow)` lub **`extern "C"`** jako niezdefiniowanego zachowania. Funkcje korzystające z tych trzech atrybutów deklaracji nie wymuszają sprawdzania zakończenia środowiska uruchomieniowego dla wyjątków. Możesz użyć **`/EHr`** opcji, aby pomóc w zidentyfikowaniu tego niezdefiniowanego zachowania, wymuszając kompilatorowi generowanie testów dla nieobsłużonych wyjątków, które ucieczką **`noexcept`** funkcję.

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>Ustawianie opcji w programie Visual Studio lub programowo

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz pozycję **Właściwości konfiguracji**  >  generowanie kodu**C/C++**  >  **Code Generation**.

1. Zmodyfikuj właściwość **Włącz wyjątki C++** .

   Lub ustaw opcję **Włącz wyjątki C++** na wartość **nie**, a następnie na stronie właściwości **wiersza polecenia** w polu **dodatkowe opcje** Dodaj kompilator opcji.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)\
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)\
[Błędy i obsługa wyjątków](../../cpp/errors-and-exception-handling-modern-cpp.md)\
[Specyfikacje wyjątków ( throw )](../../cpp/exception-specifications-throw-cpp.md)\
[Obsługa wyjątków strukturalnych (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)
