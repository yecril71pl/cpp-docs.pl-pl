---
title: /arch (x64)
ms.date: 10/01/2019
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
ms.openlocfilehash: 0ade6d9f744339ebaf38981d81334340b56080cb
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816227"
---
# <a name="arch-x64"></a>/arch (x64)

Określa architekturę generowania kodu w x64. Zobacz też [/arch (x86)](arch-x86.md) i [/arch (ARM)](arch-arm.md).

## <a name="syntax"></a>Składnia

```
/arch:[AVX|AVX2|AVX512]
```

## <a name="arguments"></a>Argumenty

**/arch: AVX**<br/>
Umożliwia korzystanie z zaawansowanych instrukcji dotyczących rozszerzeń wektorów firmy Intel.

**/arch: AVX2**<br/>
Umożliwia korzystanie z instrukcji Intel Advanced Vector Extensions 2.

**/arch: AVX512**<br/>
Umożliwia korzystanie z instrukcji 512 dla zaawansowanych rozszerzeń wektorów firmy Intel.

## <a name="remarks"></a>Uwagi

Opcja **/Arch** umożliwia korzystanie z niektórych rozszerzeń zestawu instrukcji, szczególnie w przypadku obliczeń wektorowych, dostępnych w procesorach z procesorów Intel i AMD. Ogólnie rzecz biorąc, ostatnio wprowadzone procesory mogą obsługiwać dodatkowe rozszerzenia, które są obsługiwane przez starsze procesory, chociaż należy zapoznać się z dokumentacją dla określonego procesora lub testu w celu obsługi rozszerzenia zestawu instrukcji za pomocą [__ CPUID](../../intrinsics/cpuid-cpuidex.md) przed wykonaniem kodu przy użyciu rozszerzenia zestawu instrukcji.

**/Arch** ma wpływ tylko na generowanie kodu dla funkcji natywnych. W przypadku użycia opcji [/CLR](clr-common-language-runtime-compilation.md) do kompilowania **/Arch** nie ma wpływu na generowanie kodu dla funkcji zarządzanych.

Rozszerzenia procesora mają następującą charakterystykę:

- Tryb domyślny używa instrukcji SSE2 dla skalarnych obliczeń zmiennoprzecinkowych i wektorowych. Te instrukcje umożliwiają obliczanie przy użyciu 128-bitowych wektorów o pojedynczej precyzji, podwójnej precyzji i 1, 2, 4 lub 8-bajtowych wartościach całkowitych, a także wartości skalarnych zmiennoprzecinkowych o pojedynczej precyzji i podwójnej precyzji.

- **AVX** wprowadził alternatywne kodowanie instrukcji dla wektorów i zmiennoprzecinkowych instrukcji skalarnych, które umożliwiają wektorów 128 bitów lub 256 bitów, a zero — rozszerza wszystkie wyniki wektorów do pełnego rozmiaru wektora. (W przypadku starszej zgodności, instrukcje wektora stylu SSE zachowują wszystkie bity poza bitowym 127). Większość operacji zmiennoprzecinkowych jest przedłużona do 256 bitów.

- **AVX2** rozszerza większość operacji całkowitych na 256-bitowe wektory i umożliwia korzystanie z wyrzucanych instrukcji z pomnożeniem dodawania (FMA).

- **AVX-512** wprowadza inny formularz kodowania instrukcji, który umożliwia używanie wektorów 512-bitowych i niektórych innych opcjonalnych funkcji. Dodano również instrukcje dotyczące dodatkowych operacji.

Każda opcja **/Arch** może również umożliwić użycie innych instrukcji innych niż wektorowe, które są skojarzone z tą opcją. Przykładem jest użycie pewnych instrukcji BMI, gdy określono **/arch: AVX2** .

Symbol preprocesora `__AVX__` jest definiowany, gdy określono opcję kompilatora **/arch: AVX**, **/arch: AVX2** lub **/arch: AVX512** . Symbol preprocesora `__AVX2__` jest definiowany, gdy jest określona opcja kompilatora **/arch: AVX2** lub **/arch: AVX512** . Symbole preprocesora `__AVX512F__`, `__AVX512CD__`, `__AVX512BW__`, `__AVX512DQ__` i `__AVX512VL__` są definiowane, gdy jest określona opcja kompilatora **/arch: AVX512** . Aby uzyskać więcej informacji, zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md). Opcja **/arch: AVX2** została wprowadzona w Visual Studio 2013 Update 2 w wersji 12.0.34567.1. Ograniczona obsługa **/arch: AVX512** została dodana w programie visual Studio 2017 i rozwinięta w programie visual Studio 2019.

### <a name="to-set-the-archavx-archavx2-or-archavx512-compiler-option-in-visual-studio"></a>Aby ustawić/arch: AVX,/arch: AVX2 lub/arch: AVX512, opcja kompilatora w programie Visual Studio

1. Otwórz okno dialogowe **strony właściwości** dla projektu. Aby uzyskać więcej informacji, [Zobacz C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Właściwości konfiguracji**, **C/C++**  folder.

1. Wybierz stronę właściwości **generowanie kodu** .

1. W polu listy rozwijanej **Włącz rozszerzony zestaw instrukcji** wybierz pozycję **Zaawansowane rozszerzenia wektorów (/arch: AVX)** , **Zaawansowane rozszerzenia wektorów 2 (/arch: AVX2)** lub **Zaawansowane rozszerzenia wektorów 512 (/arch: AVX512)** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Zobacz także

[/arch (Minimalna architektura procesora CPU)](arch-minimum-cpu-architecture.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
