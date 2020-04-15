---
title: /EH (Model obsługi wyjątku)
description: Przewodnik po opcjach kompilatora microsoft C++ /EH (model obsługi wyjątków) w programie Visual Studio.
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
- SEH
- try
- catch
- throw
- extern
- finally
- noexcept
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
ms.openlocfilehash: 68d6af657e7c20c0f5e84674dd91803beb35fba0
ms.sourcegitcommit: 0e4feb35b47c507947262d00349d4a893863a6d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81396293"
---
# <a name="eh-exception-handling-model"></a>/EH (Model obsługi wyjątku)

Określa obsługę modelu obsługi wyjątków generowane przez kompilator. Argumenty określają, `catch(...)` czy mają być stosowane składni do ustrukturyzowanych i standardowych throw wyjątków C++, czy **noexcept** ** extern kod "C"** zakłada się wyjątki i czy zoptymalizować niektóre kontrole.

## <a name="syntax"></a>Składnia

> **`/EHa`**[**`-`**]\
> **`/EHs`**[**`-`**]\
> **`/EHc`**[**`-`**]\
> **`/EHr`**[**`-`**]

## <a name="arguments"></a>Argumenty

**`a`**\
Umożliwia odwijanie stosu standardowego w języku C++. Połowy zarówno strukturalnych (asynchroniczne) i standardowe C++ (synchroniczne) wyjątki podczas korzystania ze `catch(...)` składni. **`/EHa`** zastępuje zarówno **`/EHs`** argumenty, jak i **`/EHc`** argumenty.

**`s`**\
Umożliwia odwijanie stosu standardowego w języku C++. Połowy tylko standardowe wyjątki C++ `catch(...)` podczas korzystania ze składni. O **`/EHc`** ile nie określono również, kompilator zakłada, throw że funkcje zadeklarowane jako ** extern "C"** może wyjątek C++.

**`c`**\
W przypadku **`/EHs`** użycia z kompilatorem zakłada, że throw funkcje zadeklarowane jako ** extern "C"** nigdy nie wyjątek C++. Nie ma wpływu, **`/EHa`** gdy jest **`/EHca`** używany z **`/EHa`**(czyli jest odpowiednikiem ). **`/EHc`** jest ignorowana, jeśli **`/EHs`** lub **`/EHa`** nie są określone.

**`r`**\
Informuje kompilator, aby zawsze generować **noexcept** sprawdzanie zakończenia środowiska uruchomieniowego dla wszystkich funkcji. Domyślnie sprawdzanie środowiska **noexcept** uruchomieniowego może być zoptymalizowany, jeśli kompilator określa funkcji wywołuje tylko funkcje nierzucając. Ta opcja zapewnia ścisłą zgodność języka C++ kosztem dodatkowego kodu. **`/EHr`** jest ignorowana, jeśli **`/EHs`** lub **`/EHa`** nie są określone.

**`-`**\
Czyści poprzedni argument opcji. Na przykład **`/EHsc-`** jest interpretowany jako **`/EHs /EHc-`**, **`/EHs`** i jest odpowiednikiem .

**`/EH`** argumenty mogą być określone oddzielnie lub połączone, w dowolnej kolejności. Jeśli określono więcej niż jedno wystąpienie tego samego argumentu, ostatni zastępuje wszystkie wcześniejsze.  Na **`/EHr- /EHc /EHs`** przykład, jest **`/EHscr-`** taka **`/EHscr- /EHr`** sama jak , **`/EHscr`** i ma taki sam efekt jak .

## <a name="remarks"></a>Uwagi

### <a name="default-exception-handling-behavior"></a>Domyślne zachowanie obsługi wyjątków

Kompilator zawsze generuje kod, który obsługuje asynchronicznego obsługi wyjątków strukturalnych (SEH). Domyślnie (oznacza to, **`/EHsc`** **`/EHs`** że **`/EHa`** jeśli nie , lub SEH opcja jest określona), `catch(...)` kompilator obsługuje programy obsługi w natywnej klauzuli C++. Jednak generuje również kod, który tylko częściowo obsługuje wyjątki C++. Domyślny wyjątek odwijania kodu nie niszczy automatycznych [try](../../cpp/try-throw-and-catch-statements-cpp.md) obiektów C++ poza blokami, które wychodzą poza zakres z powodu wyjątku. Przecieki zasobów i niezdefiniowane zachowanie może spowodować, gdy wyjątek C++.

### <a name="standard-c-exception-handling"></a>Standardowa obsługa wyjątków języka C++

Pełna obsługa kompilatora dla modelu obsługi wyjątków Standard C++, **`/EHs`** który **`/EHa`** bezpiecznie odwija obiekty stosu wymaga **`/EHsc`** (zalecane), lub .

Jeśli **`/EHs`** używasz **`/EHsc`** lub `catch(...)` , a następnie catch klauzule nie asynchroniczne wyjątki strukturalne. Wszelkie naruszenia dostępu <xref:System.Exception?displayProperty=fullName> i wyjątki zarządzane są niesłabnące. I obiekty w zakresie, gdy wystąpi wyjątek asynchroniczne nie są niszczone, nawet jeśli kod obsługuje wyjątek asynchroniczne. To zachowanie jest argumentem dla pozostawienia wyjątków strukturalnych nieobsługiwał. Zamiast tego należy wziąć pod uwagę te wyjątki jako śmiertelne.

W przypadku **`/EHs`** **`/EHsc`** użycia lub kompilator zakłada, że wyjątki mogą występować tylko w **throw** instrukcji lub wywołania funkcji. To założenie umożliwia kompilatorowi wyeliminować kod do śledzenia okresu istnienia wielu unwindable obiektów, które mogą znacznie zmniejszyć rozmiar kodu. Jeśli używasz, **`/EHa`** obraz wykonywalny może być większy i wolniejszy, ponieważ kompilator nie optymalizuje **try** bloków tak agresywnie. Pozostawia również filtry wyjątków, które automatycznie czyszczą obiekty lokalne, nawet jeśli throw kompilator nie widzi żadnego kodu, który może wyjątek języka C++.

### <a name="structured-and-standard-c-exception-handling"></a>Ustrukturyzowa i standardowa obsługa wyjątków języka C++

Opcja **`/EHa`** kompilatora umożliwia bezpieczne odwijanie stosu dla wyjątków asynchronicznych i wyjątków C++. Obsługuje obsługę zarówno standardowych wyjątków C++ i strukturalnych przy `catch(...)` użyciu natywnej klauzuli C++. Aby SEH **`/EHa`** zaimplementować bez określania , można użyć **__try,** **__except**i **__finally** składni. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków strukturalnych](../../cpp/structured-exception-handling-c-cpp.md).

> [!IMPORTANT]
> Określanie **`/EHa`** i próby obsługi wszystkich `catch(...)` wyjątków przy użyciu może być niebezpieczne. W większości przypadków wyjątki asynchroniczne są nie do odzyskania i powinny być uważane za krytyczne. Ich wychwytywanie i kontynuacja wykonania aplikacji może spowodować uszkodzenie procesu i prowadzić do błędów, które trudno znaleźć i naprawić.
>
> Mimo że systemy Windows i SEHVisual C++ obsługują obsługę , zdecydowanie zalecamy**`/EHsc`** **`/EHs`** stosowanie standardowej obsługi wyjątków języka C++ (lub ). To sprawia, że kod bardziej przenośne i elastyczne. Może być jeszcze kilka razy SEH trzeba użyć w starszym kodzie lub dla poszczególnych rodzajów programów. Jest to wymagane w kodzie skompilowanym do obsługi środowiska wykonawczego języka wspólnego ([/clr](clr-common-language-runtime-compilation.md)), na przykład. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków strukturalnych](../../cpp/structured-exception-handling-c-cpp.md).
>
> Zaleca się, aby nigdy nie **`/EHa`** łączyć plików **`/EHs`** obiektów **`/EHsc`** skompilowanych przy użyciu plików skompilowanych przy użyciu lub w tym samym module wykonywalnym. Jeśli musisz obsługiwać wyjątek asynchroniczny przy użyciu **`/EHa`** **`/EHa`** dowolnego miejsca w module, użyj do skompilowania całego kodu w module. Można użyć strukturalnej składni obsługi wyjątków w tym samym module **`/EHs`** co kod, który jest kompilowany przy użyciu . Jednak nie można mieszać SEH składni z C++ **try** **catch** **throw** i w tej samej funkcji.

Użyj, **`/EHa`** jeśli catch chcesz wyjątek, który jest wywoływany przez coś innego niż **throw**. Ten przykład generuje i wychwytuje wyjątek strukturalny:

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

### <a name="exception-handling-under-clr"></a>Obsługa wyjątków w obszarze /clr

Opcja **`/clr`** implikuje **`/EHa`** (czyli **`/clr /EHa`** jest zbędna). Kompilator generuje błąd, **`/EHs`** **`/EHsc`** jeśli lub **`/clr`** jest używany po . Optymalizacje nie wpływają na to zachowanie. Gdy wyjątek zostanie przechwycony, kompilator wywołuje destruktory klasy dla wszystkich obiektów, które znajdują się w tym samym zakresie co wyjątek. Jeśli wyjątek nie zostanie przechwycony, te destruktory nie są uruchamiane.

Aby uzyskać informacje na **`/clr`** temat ograniczeń dotyczących obsługi wyjątków w obszarze , zobacz [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md).

### <a name="runtime-exception-checks"></a>Sprawdzanie wyjątków środowiska uruchomieniowego

Opcja **`/EHr`** wymusza sprawdzanie zakończenia środowiska uruchomieniowego we wszystkich funkcjach, które mają **noexcept** atrybut. Domyślnie sprawdzanie środowiska uruchomieniowego może być zoptymalizowany, jeśli zaplecza kompilatora określa, że funkcja wywołuje tylko funkcje *nierzucając.* Funkcje niezwiązane z zgłaszaniem są wszystkie funkcje, które mają atrybut, który określa żadnych wyjątków mogą być generowane. Obejmują one **noexcept** funkcje `__declspec(nothrow)`oznaczone , **`/EHc`** `throw()`, i, gdy jest określony, ** extern "C"** funkcje. Funkcje nierzucając również wszystkie, które kompilator określił są nie rzuca przez inspekcję. Zachowanie domyślne można jawnie **`/EHr-`** ustawić za pomocą programu .

Atrybut niezwiązanym z zgłaszaniem nie jest gwarancją, że wyjątki nie mogą być generowane przez funkcję. W przeciwieństwie do **noexcept** zachowania funkcji kompilator MSVC uznaje wyjątek `throw()`zgłoszony `__declspec(nothrow)`przez funkcję zadeklarowaną przy użyciu , lub ** extern "C"** jako zachowanie niezdefiniowane. Funkcje korzystające z tych trzech atrybutów deklaracji nie wymuszają sprawdzania zakończenia środowiska uruchomieniowego dla wyjątków. Można użyć **`/EHr`** tej opcji, aby ułatwić identyfikację tego niezdefiniowanego zachowania, zmuszając kompilator do generowania kontroli środowiska uruchomieniowego dla nieobsługiwane wyjątki, które unikają **noexcept** funkcji.

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>Ustawianie opcji w programie Visual Studio lub programowo

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **Strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora języka C++ i właściwości kompilacji w programie Visual Studio.](../working-with-project-properties.md)

1. Wybierz **polecenie Generowanie** > kodu właściwości konfiguracji**C/C++** > **Code Generation**.

1. Zmodyfikuj **włącz wyjątki C++,** właściwość.

   Możesz też ustawić **opcję Włącz wyjątki C++** na **Nie**, a następnie na stronie właściwości **Wiersz polecenia** w polu **Opcje dodatkowe** dodaj opcję kompilatora.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)\
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)\
[Błędy i obsługa wyjątków](../../cpp/errors-and-exception-handling-modern-cpp.md)\
[Specyfikacje wyjątków (throw)](../../cpp/exception-specifications-throw-cpp.md)\
[Obsługa wyjątków strukturalnych (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)
