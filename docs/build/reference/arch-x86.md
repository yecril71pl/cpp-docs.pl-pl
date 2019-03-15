---
title: /arch (x86)
ms.date: 11/04/2016
ms.assetid: 9dd5a75d-06e4-4674-aade-33228486078d
ms.openlocfilehash: a429824a7c22aa9aba460481394785d31b92a5ef
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812255"
---
# <a name="arch-x86"></a>/arch (x86)

Określa architekturę do generowania kodu na x86. Zobacz też [/arch (x64)](arch-x64.md) i [/arch (ARM)](arch-arm.md).

## <a name="syntax"></a>Składnia

```
/arch:[IA32|SSE|SSE2|AVX|AVX2]
```

## <a name="arguments"></a>Argumenty

**/arch:IA32**<br/>
Określa Brak rozszerzonych instrukcji, a także określa x87 dla obliczeń zmiennopozycyjnych.

**/arch:SSE**<br/>
Włącza używanie instrukcji SSE.

**/arch:SSE2**<br/>
Włącza używanie instrukcji SSE2. Jest to domyślny instrukcji na x86 platformy, jeśli nie **/arch** określono opcję.

**/arch:AVX**<br/>
Włącza używanie instrukcji Intel Advanced Vector Extensions.

**/arch:AVX2**<br/>
Włącza używanie instrukcji Intel zaawansowany wektor rozszerzeń 2.

## <a name="remarks"></a>Uwagi

Instrukcji SSE i SSE2 istnieje na różnych procesorach Intel i AMD. Instrukcji AVX istnieje na procesorach Intel Sandy mostek i procesory AMD Bulldozer. Instrukcji AVX2 są obsługiwane przez Intel Haswell i Broadwell procesorów oraz procesorów opartych na Koparka AMD.

`_M_IX86_FP`, `__AVX__` i `__AVX2__` wskazać makra, które, jeśli są dostępne, **/arch** użyto opcji kompilatora. Aby uzyskać więcej informacji, zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md). **/Arch:AVX2** opcji i `__AVX2__` — makro zostały wprowadzone w programie Visual Studio 2013 Update 2, wersja 12.0.34567.1.

Optymalizator pozwala wybrać, kiedy i jak użyj instrukcji SSE i SSE2, gdy **/arch** jest określony. Używa ona SSE i SSE2 instrukcje dotyczące kilka skalarne obliczeń zmiennoprzecinkowych, podczas określania, czy szybciej jest używać instrukcji SSE/SSE2 i rejestrów zamiast x87 zmiennoprzecinkowych Zarejestruj stosu. W rezultacie Twój kod może faktycznie na użytek kombinację zarówno x87 SSE/SSE2 obliczeń zmiennoprzecinkowych. Ponadto za pomocą **SSE2**, instrukcje SSE2 może służyć do niektórych operacji 64-bitową liczbę całkowitą.

Oprócz przy użyciu instrukcji SSE i SSE2, kompilator używa także inne instrukcje, które znajdują się na poprawki procesora, które obsługują rozszerzenia SSE i SSE2. Przykładem jest instrukcji CMOV, która najpierw pojawiły się na procesor Pentium Pro korektą procesory Intel.

Ponieważ x86 kompilator generuje kod używającego instrukcji SSE2, domyślnie, należy określić **/arch:IA32** wyłączenie generowania instrukcji SSE i SSE2 dla x86 procesorów.

**/ arch** tylko ma wpływ na generowanie kodu dla funkcji natywnych. Kiedy używasz [/CLR](clr-common-language-runtime-compilation.md) do kompilowania, **/arch** nie ma wpływu na generowanie kodu dla funkcji zarządzanej.

**/ arch** i [/QIfist](qifist-suppress-ftol.md) nie można użyć w tym samym compiland —. W szczególności, jeśli nie używasz `_controlfp` do modyfikowania słowa sterującego FP, a następnie uruchamiania środowiska wykonawczego zestawy x87 FPU kontrolki programu word sterowanie dokładnością pola Kod do 53 bitów. W związku z tym co zmiennoprzecinkowe i podwójne operacji w wyrażeniu używa mantysę 53-bitową i wykładnik 15-bitowych. Jednak każda operacja pojedynczej precyzji SSE używa mantysę 24-bitowego i wykładnik 8-bitową i SSE2 podwójnej precyzji operacje używają mantysę 53-bitową i wykładnik 11-bitowych. Aby uzyskać więcej informacji, zobacz [_control87 —, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md). Te różnice są możliwe w drzewie jedno wyrażenie, ale nie w przypadkach, gdzie uczestniczy przypisanie użytkownika po każdym Podwyrażenie. Rozważ następujące opcje:

```cpp
r = f1 * f2 + d;  // Different results are possible on SSE/SSE2.
```

Porównaj:

```cpp
t = f1 * f2;   // Do f1 * f2, round to the type of t.
r = t + d;     // This should produce the same overall result
               // whether x87 stack is used or SSE/SSE2 is used.
```

### <a name="to-set-this-compiler-option-for-avx-avx2-ia32-sse-or-sse2-in-visual-studio"></a>Aby ustawić tę opcję kompilatora AVX, AVX2, IA32, SSE lub SSE2 w programie Visual Studio

1. Otwórz **stron właściwości** okno dialogowe dla projektu. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji**, **C/C++** folderu.

1. Wybierz **generowania kodu** stronę właściwości.

1. Modyfikowanie **Włącz rozszerzone rozkazów** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Zobacz także

[/arch (Minimalna architektura procesora CPU)](arch-minimum-cpu-architecture.md)<br/>
[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
