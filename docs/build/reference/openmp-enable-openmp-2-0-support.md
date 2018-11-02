---
title: /openmp (Włącz obsługę OpenMP 2.0)
ms.date: 11/04/2016
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
ms.openlocfilehash: 03992a0e8eef3ba9b2683ecb87809b53cb551636
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518069"
---
# <a name="openmp-enable-openmp-20-support"></a>/openmp (Włącz obsługę OpenMP 2.0)

Powoduje, że kompilator przetwarzania `#pragma` [omp](../../preprocessor/omp.md).

## <a name="syntax"></a>Składnia

```
/openmp
```

## <a name="remarks"></a>Uwagi

`#pragma omp` Służy do określania [dyrektywy](../../parallel/openmp/reference/openmp-directives.md) i [klauzule](../../parallel/openmp/reference/openmp-clauses.md). Jeśli **/OpenMP** nie została określona w zestawieniu, kompilator ignoruje klauzule OpenMP i dyrektyw. [OpenMP — funkcja](../../parallel/openmp/reference/openmp-functions.md) wywołania są przetwarzane przez kompilator, nawet jeśli **/OpenMP** nie zostanie określony.

Aplikacje skompilowane z **/OpenMP** i **/CLR** może być uruchamiany tylko w procesie domeny pojedynczej aplikacji; wiele domen aplikacji nie są obsługiwane. Oznacza to, gdy Konstruktor modułu (.cctor) jest uruchomiona, jest w stanie wykryć ten proces jest kompilowany za pomocą **/OpenMP** oraz jeśli aplikacja jest ładowany do obsługi innych niż domyślne. Aby uzyskać więcej informacji, zobacz [appdomain](../../cpp/appdomain.md), [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md), i [inicjowanie zestawów mieszanych](../../dotnet/initialization-of-mixed-assemblies.md).

Jeśli użytkownik podejmie próbę załadowania aplikacji skompilowanych za pomocą **/OpenMP** i **/CLR** do domeny aplikacji innych niż domyślne, <xref:System.TypeInitializationException> zostanie zgłoszony wyjątek poza debugerem i Zostanie zgłoszony wyjątek OpenMPWithMultipleAppdomainsException w debugerze.

Wyjątki te można podnieść w taki sposób, w następujących sytuacjach:

- Jeśli aplikacja jest kompilowana z **/CLR**, ale nie z **/OpenMP**, jest ładowany do domeny aplikacji innych niż domyślne, ale uwzględniającym procesu aplikacji, który został skompilowany przy użyciu **/ OpenMP**.

- W przypadku przekazania swojej **/CLR** aplikacji narzędzia, takie jak regasm.exe ([Regasm.exe (narzędzie rejestracji zestawów)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)), który ładuje jego zestawów docelowych do domeny aplikacji innych niż domyślne.

Zabezpieczenia dostępu kodu wykonywalnych języka wspólnego nie działa w regionach OpenMP. Jeśli zastosujesz atrybutu zabezpieczeń dostępu kodu CLR poza równoległego regionu, nie będzie obowiązywać w równoległego regionu.

Microsoft informacją o tym, że nie napiszesz **/OpenMP** aplikacji, które umożliwia częściowo zaufanych wywołań, przy użyciu <xref:System.Security.AllowPartiallyTrustedCallersAttribute>, lub atrybutów zabezpieczeń dostępu kodu CLR.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji** węzła.

1. Rozwiń **C/C++** węzła.

1. Wybierz **języka** stronę właściwości.

1. Modyfikowanie **obsługę OpenMP** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje niektóre skutków uruchomienia puli wątków, w przeciwieństwie do użycia z puli wątków po jej uruchomieniu. Dwurdzeniowy procesor puli wątków x64 jednordzeniowy, zakładając, że trwa około 16ms uruchamiania. Po tym jednak istnieje bardzo mało koszt puli wątków.

Podczas kompilacji z **/OpenMP**, drugie wywołanie test2 nigdy nie działa dłużej niż kompilacji z **/openmp-**, ponieważ nie ma żadnych uruchamiania puli wątków. Na milion iteracji **/OpenMP** wersji jest szybsza niż **/openmp-** wersji na drugie wywołanie, aby test2 i o 25 iteracji **/openmp-** i **/OpenMP** rejestru wersjami mniejszy niż stopień szczegółowości zegara.

Tak, jeśli masz tylko jedną pętli w aplikacji i działa w mniej niż 15 MS (dostosowana do przybliżony narzut na komputerze), **/OpenMP** mogą nie być odpowiednie, ale jeśli jest więcej niż ta, warto rozważyć użycie **/OpenMP**.

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

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)