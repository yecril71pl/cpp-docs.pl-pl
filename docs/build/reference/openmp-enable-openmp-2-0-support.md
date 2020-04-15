---
title: /openmp (Włącz obsługę OpenMP)
ms.date: 04/15/2019
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
ms.openlocfilehash: d3454650bfaaacd756e5cfc73df056441a39f5ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336193"
---
# <a name="openmp-enable-openmp-support"></a>/openmp (Włącz obsługę OpenMP)

Powoduje, że kompilator do przetwarzania [`#pragma omp`](../../preprocessor/omp.md) dyrektyw w celu wsparcia OpenMP.

## <a name="syntax"></a>Składnia

::: moniker range=">= vs-2019"

> **/openmp**\[**:**__eksperymentalny__]

::: moniker-end

::: moniker range="<= vs-2017"

> **/openmp**

::: moniker-end

## <a name="remarks"></a>Uwagi

`#pragma omp`służy do określania [dyrektyw](../../parallel/openmp/reference/openmp-directives.md) i [klauzul](../../parallel/openmp/reference/openmp-clauses.md). Jeśli **/openmp** nie jest określony w kompilacji, kompilator ignoruje openmp klauzule i dyrektywy. [Wywołania funkcji OpenMP](../../parallel/openmp/reference/openmp-functions.md) są przetwarzane przez kompilator, nawet jeśli **/openmp** nie jest określony.

::: moniker range=">= vs-2019"

Kompilator C++ obsługuje obecnie standard OpenMP 2.0. Jednak visual studio 2019 oferuje teraz również funkcje SIMD. Aby użyć karty SIMD, skompiluj za pomocą opcji **/openmp:experimental.** Ta opcja umożliwia zarówno zwykłe funkcje OpenMP, jak i dodatkowe funkcje OpenMP SIMD nie są dostępne podczas korzystania z przełącznika **/openmp.**

::: moniker-end

Aplikacje skompilowane przy użyciu **/openmp** i **/clr** można uruchomić tylko w procesie domeny pojedynczej aplikacji. Wiele domen aplikacji nie są obsługiwane. Oznacza to, że po`.cctor`uruchomieniu konstruktora modułu ( ) wykrywa, czy proces jest kompilowany przy użyciu **/openmp**i jeśli aplikacja jest ładowana do środowiska uruchomieniowego nie domyślnego. Aby uzyskać więcej informacji, zobacz [appdomain](../../cpp/appdomain.md), [/clr (Kompilacja środowiska wykonawczego języka wspólnego)](clr-common-language-runtime-compilation.md)i [Inicjowanie zestawów mieszanych](../../dotnet/initialization-of-mixed-assemblies.md).

Jeśli spróbujesz załadować aplikację skompilowaną przy użyciu **/openmp** i **/clr** do domeny aplikacji nie domyślnej, <xref:System.TypeInitializationException> wyjątek jest zgłaszany poza debugerem, `OpenMPWithMultipleAppdomainsException` a wyjątek jest zgłaszany w debugerze.

Wyjątki te mogą być również podniesione w następujących sytuacjach:

- Jeśli aplikacja jest skompilowana przy użyciu **/clr,** ale nie **/openmp**i jest ładowana do domeny aplikacji nie domyślnej, gdzie proces obejmuje aplikację skompilowaną przy użyciu **/openmp**.

- Jeśli przekażesz aplikację **/clr** do narzędzia, takiego jak [regasm.exe,](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)które ładuje jej zestawy docelowe do domeny aplikacji nie domyślnej.

Zabezpieczenia dostępu do kodu środowiska wykonawczego języka wspólnego nie działają w regionach OpenMP. Jeśli zastosujesz atrybut zabezpieczeń dostępu do kodu CLR poza regionem równoległym, nie będzie on obowiązywać w regionie równoległym.

Firma Microsoft nie zaleca pisania **/openmp** aplikacji, które umożliwiają częściowo zaufanych rozmówców. Nie używaj <xref:System.Security.AllowPartiallyTrustedCallersAttribute>atrybutów zabezpieczeń dostępu do kodu CLR ani żadnych atrybutów zabezpieczeń.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **Strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora języka C++ i właściwości kompilacji w programie Visual Studio.](../working-with-project-properties.md)

1. Rozwiń stronę **właściwości** > **Właściwości** języka**C/C++.** > 

1. Zmodyfikuj właściwość **Obsługa OpenMP.**

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono niektóre skutki uruchamiania puli wątków w porównaniu z przy użyciu puli wątków po jej uruchomieniu. Zakładając, że x64, jednordzeniowy, dwuprocesorowy, pula wątków zajmuje około 16 ms, aby uruchomić. Po tym, nie ma niewielkich dodatkowych kosztów dla puli wątków.

Podczas kompilowania przy użyciu **/openmp,** drugie wywołanie test2 nigdy nie jest uruchamiane dłużej niż w przypadku kompilacji przy użyciu **/openmp-**, ponieważ nie ma uruchamiania puli wątków. W przypadku miliona iteracji **/openmp** wersja jest szybsza niż wersja **/openmp-** dla drugiego wywołania do test2. W iteracjach 25 wersje **/openmp i** **/openmp** rejestrują mniej niż ziarnistość zegara.

Jeśli masz tylko jedną pętlę w aplikacji i działa w mniej niż 15 ms (dostosowane do przybliżonego narzutu na komputerze), **/openmp** może nie być odpowiednie. Jeśli jest wyższa, warto rozważyć użycie **/openmp**.

```cpp
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

[Opcje kompilatora MSVC](compiler-options.md) \
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md) \
[OpenMP w MSVC](../../parallel/openmp/openmp-in-visual-cpp.md)
