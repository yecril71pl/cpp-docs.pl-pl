---
title: /EH (Model obsługi wyjątku)
ms.date: 08/14/2018
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
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
ms.openlocfilehash: 8546b14995317afb57e4cc23a5d6f81c2172a1a6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328293"
---
# <a name="eh-exception-handling-model"></a>/EH (Model obsługi wyjątku)

Określa rodzaj obsługi wyjątków używane przez kompilator, kiedy do optymalizacji kontroli wyjątków od i czy zniszczyć C++ obiektów, które wychodzą z zakresu z powodu wyjątku. Jeśli **/EH** nie jest określony, kompilator umożliwia kod do połowu zarówno asynchroniczne wyjątki strukturalne i wyjątki C++, ale nie niszczy C++ obiektów, które wychodzą poza zakres z powodu wyjątku asynchroniiowego.

## <a name="syntax"></a>Składnia

> **/EH**{**s**|**a**}[**c][****r]**]**-**

## <a name="arguments"></a>Argumenty

**A**<br/>
Model obsługi wyjątków, który łapie zarówno asynchroniczne (strukturalne) i synchroniczne (C++) wyjątki przy użyciu składni C++. `catch(...)`

**S**<br/>
Model obsługi wyjątków, który połowy synchroniczne (C++) wyjątki tylko i mówi kompilator założyć, że funkcje zadeklarowane jako **extern "C"** może zgłosić wyjątek.

**C**<br/>
Jeśli jest używany z **s** (**/EHsc**), połowy C++ wyjątki tylko i mówi kompilator założyć, że funkcje zadeklarowane jako **extern "C"** nigdy nie zgłaszać wyjątek C++. **/EHca** jest odpowiednikiem **/EHa**.

**R**<br/>
Informuje kompilator, aby zawsze generować sprawdzanie zakończenia środowiska uruchomieniowego dla wszystkich funkcji **noexcept.** Domyślnie sprawdza, czy środowisko uruchomieniowe **nie może** być zoptymalizowany, jeśli kompilator określa, że funkcja wywołuje tylko funkcje nierzucające.

## <a name="remarks"></a>Uwagi

Opcja kompilatora **/EHa** jest używana do obsługi asynchronicznie strukturalnych wyjątków `catch(...)` (SEH) z natywną klauzulą C++. Aby zaimplementować SEH bez określania **/EHa**, można użyć **__try**, **__except**i **__finally** składni. Mimo że windows i Visual C++ obsługują SEH, zdecydowanie zaleca się używanie obsługi wyjątków C++ standard ISO (**/EHs** lub **/EHsc),** ponieważ sprawia, że kod jest bardziej przenośny i elastyczny. Niemniej jednak w istniejącym kodzie lub dla określonych rodzajów programów — na przykład w kodzie skompilowanym do obsługi środowiska wykonawczego języka wspólnego ([/clr (Kompilacja środowiska wykonawczego języka wspólnego)](clr-common-language-runtime-compilation.md))— nadal może być trzeba użyć SEH. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków strukturalnych (C/C++)](../../cpp/structured-exception-handling-c-cpp.md).

Określanie **/EHa** i próbuje obsłużyć wszystkie wyjątki przy użyciu `catch(...)` może być niebezpieczne. W większości przypadków wyjątki asynchroniczne są nie do odzyskania i powinny być uważane za krytyczne. Ich wychwytywanie i kontynuacja wykonania aplikacji może spowodować uszkodzenie procesu i prowadzić do błędów, które trudno znaleźć i naprawić.

Jeśli używasz **/EHs** lub **/EHsc**, następnie klauzuli `catch(...)` nie przechwytuje asynchroniczne wyjątki strukturalne. Naruszenia zasad <xref:System.Exception?displayProperty=fullName> dostępu i wyjątki zarządzane nie są przechwytywały, a obiekty w zakresie, gdy generowany jest wyjątek asynchroniczne, nie są niszczone, nawet jeśli obsługiwany jest wyjątek asynchroniczne.

Jeśli używasz **/EHa**, obraz może być większy i może działać mniej dobrze, ponieważ kompilator nie optymalizuje **try** bloku tak agresywnie. Pozostawia również filtry wyjątków, które automatycznie wywołują destruktory wszystkich obiektów lokalnych, nawet jeśli kompilator nie widzi żadnego kodu, który może zgłosić wyjątek języka C++. Dzięki temu bezpieczne odwijania stosu dla wyjątków asynchronicznych, a także dla wyjątków języka C++. W przypadku użycia **/EHs**kompilator zakłada, że wyjątki mogą występować tylko w instrukcji **throw** lub wywołaniu funkcji. Dzięki temu kompilator eliminuje kod śledzenia okresu istnienia wielu odwracalnych obiektów, co może znacznie zmniejszyć rozmiar kodu.

Zaleca się, aby nie łączyć obiektów skompilowanych przy użyciu **/EHa** wraz z obiektami skompilowanymi przy użyciu **/EHs** lub **/EHsc** w tym samym module wykonywalnym. Jeśli musisz obsługiwać wyjątek asynchroniczny przy użyciu **/EHa** w dowolnym miejscu w module, użyj **/EHa** do skompilowania całego kodu w module. Można użyć składni obsługi wyjątków strukturalnych w tym samym module co kod, który jest kompilowany przy użyciu **/EHs**, ale nie można mieszać składni SEH z **try**, **throw**i **catch** w tej samej funkcji.

Użyj **/EHa,** jeśli chcesz złapać wyjątek, który jest wywoływany przez coś innego niż **rzut**. Ten przykład generuje i wychwytuje wyjątek strukturalny:

```cpp
// compiler_options_EHA.cpp
// compile with: /EHa
#include <iostream>
#include <excpt.h>
using namespace std;

void fail() {   // generates SE and attempts to catch it using catch(...)
   try {
      int i = 0, j = 1;
      j /= i;   // This will throw a SE (divide by zero).
      printf("%d", j);
   }
   catch(...) {   // catch block will only be executed under /EHa
      cout<<"Caught an exception in catch(...)."<<endl;
   }
}

int main() {
   __try {
      fail();
   }

   // __except will only catch an exception here
   __except(EXCEPTION_EXECUTE_HANDLER) {
      // if the exception was not caught by the catch(...) inside fail()
      cout << "An exception was caught in __except." << endl;
   }
}
```

Opcja **/EHc** wymaga określenia **/EHs** lub **/EHa.** **/clr** Opcja oznacza **/EHa** (czyli **/clr** **/EHa** jest nadmiarowy). Kompilator generuje błąd, jeśli **/EHs** lub **/EHsc** jest używany po **/clr**. Optymalizacje nie wpływają na to zachowanie. Gdy zostaje przechwycony wyjątek, kompilator wywołuje destruktor klasy lub destruktory obiektu lub obiektów, które znajdują się w tym samym zakresie, co wyjątek. Gdy nie przechwycono wyjątku, te destruktory nie są uruchamiane.

Aby uzyskać informacje na temat ograniczeń dotyczących obsługi wyjątków w obszarze **/clr**, zobacz [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md).

Opcję można wyczyścić za pomocą **-** symbolu . Na przykład **/EHsc-** jest interpretowany jako **/EHs** **/EHc-** i jest odpowiednikiem **/EHs**.

Opcja kompilatora **/EHr** wymusza sprawdzanie zakończenia środowiska uruchomieniowego we wszystkich funkcjach, które mają atrybut **noexcept.** Domyślnie sprawdzanie środowiska uruchomieniowego może być zoptymalizowany, jeśli zaplecza kompilatora określa, że funkcja wywołuje tylko funkcje *nierzucając.* Funkcje niezwiązane z zgłaszaniem są wszystkie funkcje, które mają atrybut, który określa żadnych wyjątków mogą być generowane. Obejmuje to funkcje oznaczone `throw()` `__declspec(nothrow)` **noexcept**, , i, gdy **/EHc** jest określony, **extern "C"** funkcje. Funkcje nierzucając również wszystkie, które kompilator określił są nie rzuca przez inspekcję. Wartość domyślną można jawnie ustawić za pomocą **/EHr-**.

Jednak atrybut niezrzucanie nie jest gwarancją, że żadne wyjątki mogą być generowane przez funkcję. W przeciwieństwie do zachowania funkcji **noexcept** kompilator MSVC uznaje wyjątek `throw()` `__declspec(nothrow)`zgłoszony przez funkcję zadeklarowaną przy użyciu , lub **extern "C"** jako zachowanie niezdefiniowane. Funkcje, które używają tych trzech atrybutów deklaracji nie wymuszaj sprawdzania zakończenia środowiska uruchomieniowego dla wyjątków. Można użyć **/EHr** opcji, aby ułatwić identyfikację tego niezdefiniowanego zachowania, zmuszając kompilator do generowania kontroli środowiska uruchomieniowego dla nieobsługiwane wyjątki, które unikną **funkcji noexcept.**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **Strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora języka C++ i właściwości kompilacji w programie Visual Studio.](../working-with-project-properties.md)

1. Wybierz **polecenie Generowanie** > kodu właściwości konfiguracji**C/C++** > **Code Generation**.

1. Zmodyfikuj **włącz wyjątki C++,** właściwość.

   Możesz też ustawić **opcję Włącz wyjątki C++** na **Nie**, a następnie na stronie właściwości **Wiersz polecenia** w polu **Opcje dodatkowe** dodaj opcję kompilatora.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Błędy i obsługa wyjątków](../../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Specyfikacje wyjątków (throw)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)
