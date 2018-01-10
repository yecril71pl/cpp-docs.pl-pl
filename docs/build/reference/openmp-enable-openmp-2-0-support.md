---
title: "-openmp (Włącz obsługę OpenMP 2.0) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
dev_langs: C++
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a8d3aaeb5d3e71dfced4bf78384a62898d99a5ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="openmp-enable-openmp-20-support"></a>/openmp (Włącz obsługę OpenMP 2.0)
Powoduje, że kompilator przetworzyć `#pragma` [omp](../../preprocessor/omp.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
/openmp  
```  
  
## <a name="remarks"></a>Uwagi  
 `#pragma omp`Służy do określania [dyrektywy](../../parallel/openmp/reference/openmp-directives.md) i [klauzule](../../parallel/openmp/reference/openmp-clauses.md). Jeśli **/OpenMP** nie została określona w kompilacji, kompilator ignoruje klauzule OpenMP i dyrektywy. [OpenMP — funkcja](../../parallel/openmp/reference/openmp-functions.md) wywołania są przetwarzane przez kompilator, nawet jeśli **/OpenMP** nie jest określona.  
  
 Aplikacja jest skompilowana przy użyciu **/OpenMP** i przy użyciu [biblioteki](../../parallel/openmp/reference/openmp-libraries.md) można uruchomić tylko w systemie Windows 2000 lub nowszych systemów operacyjnych.  
  
 Aplikacje skompilowane z **/OpenMP** i **/CLR** może być uruchamiany tylko w procesie domeny pojedynczej aplikacji; wielu domen aplikacji nie są obsługiwane. Oznacza to, gdy Konstruktor modułów (.cctor) jest uruchamiana, wykryje on proces jest skompilowana przy użyciu **/OpenMP** i jeśli aplikacja jest ładowany do obsługi innych niż domyślne. Aby uzyskać więcej informacji, zobacz [elementu appdomain](../../cpp/appdomain.md), [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md), i [inicjowanie zestawów mieszanych](../../dotnet/initialization-of-mixed-assemblies.md).  
  
 Jeśli próba załadowania aplikacji kompilowane przy użyciu **/OpenMP** i **/CLR** w domenie aplikacji innych niż domyślne <xref:System.TypeInitializationException> zostanie wygenerowany wyjątek poza debugerem i OpenMPWithMultipleAppdomainsException zostanie wygenerowany wyjątek w debugerze.  
  
 Wyjątki te można również wygenerowany w następujących sytuacjach:  
  
-   Jeśli aplikacja jest skompilowana przy użyciu **/CLR**, lecz nie **/OpenMP**, został załadowany w domenie aplikacji innych niż domyślne, ale jeśli proces obejmuje aplikację, która została skompilowana z **/ OpenMP**.  
  
-   W przypadku przekazania Twojej **/CLR** aplikacji narzędzia, takie jak regasm.exe ([Regasm.exe (narzędzie rejestracji zestawów)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)), który ładuje jego zestawów docelowych do domeny aplikacji innych niż domyślne.  
  
 Zabezpieczenia dostępu kodu języka uruchomieniowego nie działa w regionach OpenMP. W przypadku zastosowania atrybutu zabezpieczeń dostępu kodu CLR poza równoległego regionu, nie będzie obowiązywać w równoległego regionu.  
  
 Microsoft informacją o tym, że użytkownik nie zapisuj **/OpenMP** aplikacji, które zezwala na częściowo zaufane obiekty wywołujące, przy użyciu <xref:System.Security.AllowPartiallyTrustedCallersAttribute>, lub atrybutów zabezpieczeń dostępu kodu CLR.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzła.  
  
3.  Rozwiń węzeł **C/C++** węzła.  
  
4.  Wybierz **języka** strony właściwości.  
  
5.  Modyfikowanie **obsługę OpenMP** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia niektóre skutków uruchomienia puli wątków w porównaniu z użyciem pozostawiło po jej uruchomieniu. Procesor dwurdzeniowy puli wątków przy założeniu x64 pojedynczego rdzenia trwa około 16 MS uruchamiania. Po tym jednak istnieje bardzo mało koszt dla puli wątków.  
  
 Podczas kompilacji z **/OpenMP**, drugie wywołanie test2 nigdy nie uruchamia dłużej niż kompilacja z **/openmp-**, ponieważ nie ma żadnych uruchomienia puli wątków. W iteracji milion **/OpenMP** jest szybsza niż wersja **/openmp-** wersji drugie wywołanie do test2 i po 25 iteracji **/openmp-** i **/OpenMP** rejestru wersjami mniejszy niż stopień szczegółowości zegara.  
  
 Tak, jeśli masz tylko jedną pętli w aplikacji i uruchomieniu na mniej niż 15 MS (dostosowana do przybliżonej obciążenie komputera), **/OpenMP** mogą nie być odpowiednie, ale jeśli jest więcej niż warto rozważyć użycie **/OpenMP**.  
  
```  
// cpp_compiler_options_openmp.cpp  
#include <omp.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <windows.h>  
  
volatile DWORD dwStart;  
volatile int global = 0;  
  
double test2(int num_steps) {  
   int i;  
   global++;  
   double x, pi, sum = 0.0, step;  
  
   step = 1.0 / (double) num_steps;  
  
   #pragma omp parallel for reduction(+:sum) private(x)  
   for (i = 1; i <= num_steps; i++) {  
      x = (i - 0.5) * step;  
      sum = sum + 4.0 / (1.0 + x*x);  
   }  
  
   pi = step * sum;  
   return pi;  
}  
  
int main(int argc, char* argv[]) {  
   double   d;  
   int n = 1000000;  
  
   if (argc > 1)  
      n = atoi(argv[1]);  
  
   dwStart = GetTickCount();  
   d = test2(n);  
   printf_s("For %d steps, pi = %.15f, %d milliseconds\n", n, d, GetTickCount() - dwStart);  
  
   dwStart = GetTickCount();  
   d = test2(n);  
   printf_s("For %d steps, pi = %.15f, %d milliseconds\n", n, d, GetTickCount() - dwStart);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)