---
title: / OpenMP (Włącz obsługę OpenMP)
ms.date: 04/15/2019
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
ms.openlocfilehash: caa06d89c590abd2b3a74a5a6b118d6ba4acd910
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320217"
---
# <a name="openmp-enable-openmp-support"></a>/ OpenMP (Włącz obsługę OpenMP)

Powoduje, że kompilator przetwarzania [ `#pragma omp` ](../../preprocessor/omp.md) dyrektywy w odniesieniu do OpenMP.

## <a name="syntax"></a>Składnia

::: moniker range=">= vs-2019"

> **/ openmp**\[**:**__eksperymentalne__]

::: moniker-end

::: moniker range="<= vs-2017"

> **/ OpenMP**

::: moniker-end

## <a name="remarks"></a>Uwagi

`#pragma omp` Służy do określania [dyrektywy](../../parallel/openmp/reference/openmp-directives.md) i [klauzule](../../parallel/openmp/reference/openmp-clauses.md). Jeśli **/OpenMP** nie został określony w zestawieniu, kompilator ignoruje klauzule OpenMP i dyrektyw. [OpenMP — funkcja](../../parallel/openmp/reference/openmp-functions.md) wywołania są przetwarzane przez kompilator, nawet jeśli **/OpenMP** nie został określony.

::: moniker range=">= vs-2019"

C++ Kompilator obsługuje obecnie standard OpenMP 2.0. Visual Studio 2019 oferuje teraz również SIMD funkcji. Aby użyć SIMD, kompilowania przy użyciu **/OpenMP: eksperymentalne** opcji. Ta opcja umożliwia zarówno zwykłe funkcje OpenMP i dodatkowe SIMD OpenMP — funkcje nie są dostępne podczas korzystania **/OpenMP** przełącznika.

::: moniker-end

Aplikacje skompilowane przy użyciu zarówno **/OpenMP** i **/CLR** może być uruchamiany tylko w procesie domeny pojedynczej aplikacji. Wiele domen aplikacji nie są obsługiwane. Oznacza to, gdy Konstruktor modułu (`.cctor`) jest uruchomiony, wykryje to, jeśli proces jest skompilowana przy użyciu **/OpenMP**, oraz jeśli aplikacja jest ładowany do obsługi innych niż domyślne. Aby uzyskać więcej informacji, zobacz [appdomain](../../cpp/appdomain.md), [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](clr-common-language-runtime-compilation.md), i [inicjowanie zestawów mieszanych](../../dotnet/initialization-of-mixed-assemblies.md).

Jeśli użytkownik podejmie próbę załadowania aplikacji skompilowanych przy użyciu zarówno **/OpenMP** i **/CLR** do domeny aplikacji innych niż domyślne, <xref:System.TypeInitializationException> poza debugerem, jest zgłaszany wyjątek i `OpenMPWithMultipleAppdomainsException` wyjątku generowany jest debugera.

Wyjątki te można podnieść w taki sposób, w następujących sytuacjach:

- Jeśli aplikacja jest kompilowana, za pomocą **/CLR** , ale nie **/OpenMP**i jest ładowany do domeny aplikacji innych niż domyślne, obejmującym aplikacja skompilowana przy użyciu procesu   **/OpenMP**.

- W przypadku przekazania swojej **/CLR** aplikacji do narzędzia, takie jak [regasm.exe](/dotnet/framework/tools/regasm-exe-assembly-registration-tool), który ładuje jego zestawów docelowych do domeny aplikacji innych niż domyślne.

Zabezpieczenia dostępu kodu wykonywalnych języka wspólnego nie działa w regionach OpenMP. Jeśli zastosujesz atrybutu zabezpieczeń dostępu kodu CLR poza równoległego regionu, nie będzie obowiązywać w równoległego regionu.

Microsoft nie zaleca się, że piszesz **/OpenMP** aplikacje, które umożliwiają częściowo zaufanych obiektów wywołujących. Nie używaj <xref:System.Security.AllowPartiallyTrustedCallersAttribute>, lub atrybutów zabezpieczeń dostępu kodu CLR.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji** > **C /C++** > **języka** stronę właściwości.

1. Modyfikowanie **obsługę OpenMP** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje niektóre skutków uruchomienia puli wątków w przeciwieństwie do użycia w puli wątków po jego uruchomieniu. Zakładając, że x64, jednordzeniowy, dwurdzeniowy procesor puli wątków zajmuje około 16 ms mogła się uruchomić. Po tym, jest nieco dodatkowych kosztów dla puli wątków.

Gdy kompilujesz przy użyciu **/OpenMP**, drugie wywołanie test2 nigdy nie działa dłużej niż w przypadku kompilowania przy użyciu **/openmp-**, ponieważ nie ma żadnych uruchamiania puli wątków. Na milion iteracji **/OpenMP** wersji jest szybsza niż **/openmp-** wersja drugie wywołanie test2. Po 25 iteracji zarówno **/openmp-** i **/OpenMP** rejestru wersjami mniejszy niż stopień szczegółowości zegara.

Jeśli masz tylko jedną pętli w aplikacji i działa w mniej niż 15 ms (dostosowana do przybliżony narzut na komputerze), **/OpenMP** mogą nie być odpowiednie. Jeśli jest ona wyższa, warto rozważyć użycie **/OpenMP**.

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

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md) \
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md) \
[OpenMP w programie MSVC](../../parallel/openmp/openmp-in-visual-cpp.md)
