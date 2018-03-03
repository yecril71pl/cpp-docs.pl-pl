---
title: "-EH (Model obsługi wyjątku) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExceptionHandling
- /eh
- VC.Project.VCCLCompilerTool.ExceptionHandling
dev_langs:
- C++
helpviewer_keywords:
- exception handling, compiler model
- cl.exe compiler, exception handling
- EH compiler option [C++]
- -EH compiler option [C++]
- /EH compiler option [C++]
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1c56020d5013e951d9d43ed799d34641d114d612
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="eh-exception-handling-model"></a>/EH (Model obsługi wyjątku)
Określa rodzaj obsługi wyjątku przez kompilator, gdy w celu zoptymalizowania wyjątek zadań sprawdza i czy zniszczyć obiektów C++, które wykraczają poza zakres z powodu wyjątku. Jeśli **/EH** nie zostanie określony, kompilator połowy zarówno asynchroniczne wyjątki strukturalne i wyjątków języka C++, ale nie niszczy obiektami C++, które wykraczają poza zakres ze względu na wyjątek asynchroniczny.  
  
## <a name="syntax"></a>Składnia  
  
```  
/EH{s|a}[c][r][-]  
```  
  
## <a name="arguments"></a>Argumenty  
 **a**  
 Model obsługi wyjątków, który wyłapuje i wyjątki asynchroniczne (strukturalne), i synchroniczne (C++).  
  
 **s**  
 Model obsługi wyjątków, który przechwytuje tylko wyjątki C++ i informuje kompilator, aby założono, że funkcje deklarowane jako `extern "C"` może zgłosić wyjątek.  
  
 **c**  
 Jeśli jest używana z **s** (**/ehsc**), przechwytuje tylko wyjątki C++ i informuje kompilator, aby założono, że funkcje deklarowane jako `extern "C"` nigdy nie zgłaszają wyjątków C++.  
  
 **/ EHca** jest odpowiednikiem **/eha**.  
  
 **r**  
 Informuje kompilator, aby zawsze Generuj operacje sprawdzania zakończenia środowiska uruchomieniowego dla wszystkich `noexcept` funkcji. Domyślnie sprawdza środowiska uruchomieniowego `noexcept` może optymalizacji Jeśli kompilator Określa funkcje tylko innych niż wyrzucające wywołania funkcji.  
  
## <a name="remarks"></a>Uwagi  
 **/Eha** — opcja kompilatora jest używana do obsługi Obsługa wyjątków asynchronicznych strukturalne (SEH) z natywnych języka C++ `catch(...)` klauzuli. Aby zaimplementować SEH bez określania **/eha**, możesz użyć `__try`, `__except`, i `__finally` składni. Mimo że systemu Windows i program Visual C++ obsługuje SEH, zdecydowanie zaleca się używanie normy ISO C++, obsługa wyjątków (**/EHS** lub **/ehsc**) ponieważ sprawia, że kod bardziej przenośne i elastyczne. Niemniej jednak w przypadku istniejącego kodu lub dla konkretnego rodzaje programów — na przykład w kodzie skompilowanym do obsługi środowisko uruchomieniowe języka wspólnego ([/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md)) — nadal może należy użyć SEH. Aby uzyskać więcej informacji, zobacz [strukturalnych obsługi wyjątków (C/C++)](../../cpp/structured-exception-handling-c-cpp.md).  
  
 Określanie **/eha** i próby obsługiwać wszystkie wyjątki przy użyciu `catch(...)` może być niebezpieczne. W większości przypadków wyjątki asynchroniczne są nie do odzyskania i powinny być uważane za krytyczne. Ich wychwytywanie i kontynuacja wykonania aplikacji może spowodować uszkodzenie procesu i prowadzić do błędów, które trudno znaleźć i naprawić.  
  
 Jeśli używasz **/EHS** lub **/ehsc**, a następnie z `catch(...)` klauzuli catch nie asynchroniczne wyjątki strukturalne. Naruszenie zasad dostępu i zarządzane <xref:System.Exception?displayProperty=fullName> wyjątków nie są przechwytywane i obiekty w zasięgu, gdy zostanie wygenerowany wyjątek asynchroniczny nie zostaną zniszczone nawet wtedy, gdy asynchroniczne wyjątek jest obsługiwany.  
  
 Jeśli używasz **/eha**, obrazu może być większy i mogą wykonywać mniej także, ponieważ kompilator nie optymalizuje `try` jako agresywnie zablokować. Również pozostawia w filtry wyjątków, które automatycznie wywołać destruktorów wszystkich obiektów lokalnych, nawet wtedy, gdy kompilator nie widzi kodu, który może zgłaszać wyjątków C++. Dzięki temu odwijanie asynchroniczne wyjątki, jak również wyjątki C++ bezpieczne stosu. Jeśli używasz **/EHS**, kompilator zakłada wyjątki mogą występować tylko w `throw` instrukcji lub na wywołanie funkcji. Dzięki temu kompilator eliminuje kod śledzenia okresu istnienia wielu odwracalnych obiektów, co może znacznie zmniejszyć rozmiar kodu.  
  
 Firma Microsoft zaleca nie łączy obiektów kompilowanych przy użyciu **/eha** wraz z obiektów kompilowanych przy użyciu **/EHS** w tym samym module pliku wykonywalnego. Jeśli masz do obsługi wyjątków asynchronicznych za pomocą **/eha** dowolne miejsce w module, użyj **/eha** skompilować cały kod w module. Można użyć składni, w tym samym module jako kod, który ma być kompilowana przy użyciu obsługi wyjątków strukturalnych **/EHS**, ale nie można mieszać składni SEH z `try`, `throw`, i `catch` w tej samej funkcji.  
  
 Użyj **/eha** jeśli ma zostać przechwycony wyjątek, który zostanie wywołane przez coś innego niż `throw`. Ten przykład generuje i wychwytuje wyjątek strukturalny:  
  
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
  
 **Opcja/ehc** opcja wymaga, aby **/EHS** lub **/eha** jest określona. **/CLR** opcji pociąga za sobą **/eha** (to znaczy **/eha/CLR** jest nadmiarowy). Kompilator generuje błąd, jeśli **/EHS [c]** służy po **/CLR**. Optymalizacje nie wpływają na to zachowanie. Gdy zostaje przechwycony wyjątek, kompilator wywołuje destruktor klasy lub destruktory obiektu lub obiektów, które znajdują się w tym samym zakresie, co wyjątek. Gdy nie przechwycono wyjątku, te destruktory nie są uruchamiane.  
  
 Informacji o ograniczenia wynikające z obsługi wyjątków **/CLR**, zobacz [_set_se_translator —](../../c-runtime-library/reference/set-se-translator.md).  
  
 Opcja można wyczyścić za pomocą symbolu  **-** . Na przykład **/EHsc-** jest interpretowana jako **/EHc-/EHS** i stanowi odpowiednik **/EHS**.  
  
 **/EHr** — opcja kompilatora wymusza sprawdzania zakończenia środowiska uruchomieniowego w wszystkie funkcje, które mają `noexcept` atrybutu. Domyślnie sprawdzanie czasu wykonania może w celu optymalizacji Jeśli wewnętrznych kompilatora określa funkcja tylko wywołuje *-zgłaszanie* funkcji. Funkcje wyrzucające nie są wszystkie funkcje, które mają atrybut określający, że żadne wyjątki może zostać zgłoszony. Dotyczy to również funkcje oznaczone `noexcept`, `throw()`, `__declspec(nothrow)`i kiedy **opcja/ehc** jest określony, `extern "C"` funkcji. Funkcje wyrzucające nie obejmują które kompilator stwierdził są z systemem innym niż wyrzucające przez inspekcji. Należy jawnie określić domyślny przy użyciu **/EHr-**.  
  
 Jednak-zgłaszanie atrybut nie jest gwarancji, że żadne wyjątki może zostać wygenerowany przez funkcję. W przeciwieństwie do zachowania `noexcept` funkcji kompilatora Visual C++ uwzględnia wyjątek zgłoszony przez funkcję zadeklarowane za pomocą `throw()`, `__declspec(nothrow)`, lub `extern "C"` jako niezdefiniowane zachowanie. Funkcje korzystające z tych trzech deklaracji atrybutów nie wymuszają sprawdzania zakończenia środowiska uruchomieniowego dla wyjątków. Można użyć **/EHr** opcję, aby zidentyfikować ten niezdefiniowane zachowanie, powodując, że kompilator sprawdza, czy środowisko uruchomieniowe nieobsługiwanych wyjątków, które escape wygenerować `noexcept` funkcji.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  W okienku po lewej stronie rozwiń **właściwości konfiguracji**, **C/C++**, **generowania kodu**.  
  
3.  Modyfikowanie **włącz wyjątki C++** właściwości.  
  
     Lub ustaw **włącz wyjątki C++** do **nr**, a następnie na **wiersza polecenia** strony właściwości, **dodatkowe opcje** Dodaj — Opcja kompilatora.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [Błędy w obsłudze wyjątków](../../cpp/errors-and-exception-handling-modern-cpp.md)   
 [Specyfikacje wyjątków (throw)](../../cpp/exception-specifications-throw-cpp.md)   
 [Obsługa wyjątków strukturalnych (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)