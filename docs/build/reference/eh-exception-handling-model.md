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
ms.openlocfilehash: 9f5eed60ecb51abc1d8fbd3c38773bbf782b23a5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271804"
---
# <a name="eh-exception-handling-model"></a>/EH (Model obsługi wyjątku)

Określa rodzaj obsługi wyjątku przez kompilator, gdy Optymalizacja odkładania wyjątek sprawdza oraz czy niszczy obiektów C++, które wykraczają poza zakres z powodu wyjątku. Jeśli **/EH** nie zostanie określony, kompilator zapewnia swój kod, aby przechwytywać wyjątki C++ i asynchroniczne wyjątki strukturalne, ale nie niszczy obiektów C++, które wykraczają poza zakres z powodu wyjątku asynchronicznego.

## <a name="syntax"></a>Składnia

> **/EH**{**s**|**a**}[**c**][**r**][**-**]

## <a name="arguments"></a>Argumenty

**a**<br/>
Model obsługi wyjątków, który wyłapuje asynchroniczne (strukturalne) i synchronicznej wyjątków (C++) przy użyciu języka c++ `catch(...)` składni.

**s**<br/>
Model obsługi wyjątków, który przechwytuje synchronicznej wyjątków (C++) i informuje kompilator, aby założył, że funkcje zadeklarowane jako **extern "C"** może zgłosić wyjątek.

**c**<br/>
Jeśli używane **s** (**/ehsc**), wychwytuje tylko wyjątki C++ i informuje kompilator, aby założył, że funkcje zadeklarowane jako **extern "C"** nigdy nie zgłaszają wyjątków C++. **/ EHca** jest odpowiednikiem **/eha**.

**r**<br/>
Informuje kompilator, aby zawsze Generuj operacje sprawdzania zakończenia środowiska uruchomieniowego dla wszystkich **noexcept** funkcji. Domyślnie środowisko uruchomieniowe sprawdza, czy **noexcept** może optymalizacji Jeśli kompilator określa funkcja wywołuje tylko niezgłaszające funkcje.

## <a name="remarks"></a>Uwagi

**/Eha** — opcja kompilatora jest używana do obsługi asynchronicznego strukturalna Obsługa wyjątków (SEH) za pomocą natywnego języka C++ `catch(...)` klauzuli. Aby zaimplementować SEH bez określania **/eha**, może używać **__try**, **__except**, i **__finally** składni. Mimo że Windows i Visual C++ obsługuje SEH, zdecydowanie zalecamy używanie obsługi wyjątków ISO standard C++ (**/EHS** lub **/ehsc**), ponieważ dzięki niej kod jest bardziej przenośny i elastyczny. Niemniej jednak w istniejącym kodzie lub dla szczególnych typów programów — na przykład w kodzie skompilowanym z obsługą środowiska uruchomieniowego języka wspólnego ([/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](clr-common-language-runtime-compilation.md)) — nadal może być konieczne używanie SEH. Aby uzyskać więcej informacji, zobacz [obsługi wyjątków strukturalnych, (C/C++)](../../cpp/structured-exception-handling-c-cpp.md).

Określanie **/eha** i próba obsługi wszystkich wyjątków za pomocą `catch(...)` może być niebezpieczne. W większości przypadków wyjątki asynchroniczne są nie do odzyskania i powinny być uważane za krytyczne. Ich wychwytywanie i kontynuacja wykonania aplikacji może spowodować uszkodzenie procesu i prowadzić do błędów, które trudno znaleźć i naprawić.

Jeśli używasz **/EHS** lub **/ehsc**, wówczas `catch(...)` klauzuli nie wychwytuje asynchronicznych wyjątków strukturalnych. Naruszenia zasad dostępu i zarządzane <xref:System.Exception?displayProperty=fullName> wyjątki nie są przechwytywane i obiekty w zakresie podczas generowania wyjątku asynchronicznego nie są niszczone, nawet jeśli asynchroniczny wyjątek jest obsługiwany.

Jeśli używasz **/eha**, obraz, który może być większy i może wykonać mniej dobrze, ponieważ kompilator nie optymalizuje **spróbuj** tak agresywnie. Również pozostawia filtry wyjątków, które automatycznie wywołują destruktory wszystkich obiektów lokalnych, nawet jeśli kompilator nie widzi żadnego kodu, który może zgłosić wyjątek języka C++. Umożliwia to bezpieczne odwracanie stosu dla wyjątków asynchronicznych oraz wyjątków C++. Kiedy używasz **/EHS**, kompilator zakłada, że wyjątki mogą znajdować się tylko na **throw** instrukcji lub w wywołaniu funkcji. Dzięki temu kompilator eliminuje kod śledzenia okresu istnienia wielu odwracalnych obiektów, co może znacznie zmniejszyć rozmiar kodu.

Firma Microsoft zaleca, aby nie łączyć obiektów skompilowanych przy użyciu **/eha** z obiektami skompilowanymi przy użyciu **/EHS** lub **/ehsc** w tym samym module pliku wykonywalnego. Jeśli trzeba obsługiwać wyjątek asynchroniczny przy użyciu **/eha** gdziekolwiek w module, użyj **/eha** do skompilowania całego kodu w module. Możesz użyć składni, w tym samym module co kod jest kompilowany przy użyciu obsługi wyjątków strukturalnych **/EHS**, ale nie możesz mieszać składni SEH z **spróbuj**, **throw**i **catch** w tej samej funkcji.

Użyj **/eha** Jeśli chcesz przechwytywać wyjątek, który jest wywoływany przez coś innego niż **throw**. Ten przykład generuje i wychwytuje wyjątek strukturalny:

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

**Opcja/ehc** opcja wymaga, aby **/EHS** lub **/eha** jest określony. **/CLR** oznacza opcji **/eha** (czyli **/CLR** **/eha** jest nadmiarowy). Kompilator generuje błąd, jeśli **/EHS** lub **/ehsc** jest używany po **/CLR**. Optymalizacje nie wpływają na to zachowanie. Gdy zostaje przechwycony wyjątek, kompilator wywołuje destruktor klasy lub destruktory obiektu lub obiektów, które znajdują się w tym samym zakresie, co wyjątek. Gdy nie przechwycono wyjątku, te destruktory nie są uruchamiane.

Aby uzyskać informacje na temat ograniczeń obsługi wyjątków w **/CLR**, zobacz [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md).

Opcja może być obsadzona przez przy użyciu symbolu **-**. Na przykład **/EHsc-** jest interpretowany jako **/EHS** **/EHc-** i jest odpowiednikiem **/EHS**.

**/EHr** — opcja kompilatora wymusza operacje sprawdzania zakończenia środowiska uruchomieniowego w wszystkie funkcje, które mają **noexcept** atrybutu. Domyślnie testy środowiska uruchomieniowego może być w celu optymalizacji Jeśli zapleczu kompilatora okaże się, czy funkcja tylko wywołuje *niezgłaszające* funkcji. Zgłaszanie inne niż funkcje są wszystkie funkcje, które mają atrybut określający, że żadne wyjątki, które mogą być generowane. W tym funkcje oznaczone **noexcept**, `throw()`, `__declspec(nothrow)`i kiedy **opcja/ehc** jest określony, **extern "C"** funkcji. Zgłaszanie inne niż funkcje także tych, które kompilator ustalił, czy niezgłaszające inspekcja. Wartość domyślna została jawnie ustawiona przy użyciu **/EHr-**.

Jednak atrybut niezgłaszające jest gwarancję, że żadne wyjątki mogą być generowane przez funkcję. W odróżnieniu od zachowania **noexcept** funkcji, za pomocą kompilatora MSVC uwzględnia wyjątek zgłoszony przez funkcje zadeklarowane za pomocą `throw()`, `__declspec(nothrow)`, lub **extern "C"** jako niezdefiniowane zachowanie. Funkcje korzystające z tych trzech deklaracji atrybutów nie wymuszają operacje sprawdzania zakończenia środowiska uruchomieniowego do obsługi wyjątków. Możesz użyć **/EHr** opcję, aby pomóc w zidentyfikowaniu to niezdefiniowane zachowanie, wymuszając kompilatorowi Generowanie testy środowiska uruchomieniowego dla nieobsłużonych wyjątków, które ucieczki **noexcept** funkcji.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **generowanie kodu**.

1. Modyfikowanie **włącz wyjątki C++** właściwości.

   Lub ustaw **włącz wyjątki C++** do **nie**, a następnie na **wiersza polecenia** stronie właściwości, **dodatkowe opcje** Dodaj — Opcja kompilatora.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Błędy w obsłudze wyjątków](../../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Specyfikacje wyjątków (throw)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)
