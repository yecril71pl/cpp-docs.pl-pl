---
title: /arch (x86)
ms.date: 10/01/2019
ms.assetid: 9dd5a75d-06e4-4674-aade-33228486078d
ms.openlocfilehash: b1e5501f6edd3eb016395380ff476250c0c388b9
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816317"
---
# <a name="arch-x86"></a>/arch (x86)

Określa architekturę generowania kodu w architekturze x86. Zobacz też [/arch (x64)](arch-x64.md) i [/arch (ARM)](arch-arm.md).

## <a name="syntax"></a>Składnia

```
/arch:[IA32|SSE|SSE2|AVX|AVX2|AVX512]
```

## <a name="arguments"></a>Argumenty

**/arch: IA32**<br/>
Określa brak rozszerzonych instrukcji i określa x87 dla obliczeń zmiennoprzecinkowych.

**/arch: SSE**<br/>
Umożliwia korzystanie z instrukcji SSE.

**/arch: SSE2**<br/>
Umożliwia korzystanie z instrukcji SSE2. Jest to domyślna instrukcja na platformach x86, jeśli nie określono opcji **/Arch** .

**/arch: AVX**<br/>
Umożliwia korzystanie z zaawansowanych instrukcji dotyczących rozszerzeń wektorów firmy Intel.

**/arch: AVX2**<br/>
Umożliwia korzystanie z instrukcji Intel Advanced Vector Extensions 2.

**/arch: AVX512**<br/>
Umożliwia korzystanie z instrukcji 512 dla zaawansowanych rozszerzeń wektorów firmy Intel.

## <a name="remarks"></a>Uwagi

Opcja **/Arch** włącza lub wyłącza korzystanie z niektórych rozszerzeń zestawu instrukcji, szczególnie w przypadku obliczeń wektorowych, dostępnych w procesorach z procesorów Intel i AMD. Ogólnie rzecz biorąc, ostatnio wprowadzone procesory mogą obsługiwać dodatkowe rozszerzenia, które są obsługiwane przez starsze procesory, chociaż należy zapoznać się z dokumentacją dla określonego procesora lub testu w celu obsługi rozszerzenia zestawu instrukcji przy użyciu [__cpuid](../../intrinsics/cpuid-cpuidex.md) przed wykonaniem kodu przy użyciu rozszerzenia zestawu instrukcji.

**/Arch** ma wpływ tylko na generowanie kodu dla funkcji natywnych. W przypadku użycia opcji [/CLR](clr-common-language-runtime-compilation.md) do kompilowania **/Arch** nie ma wpływu na generowanie kodu dla funkcji zarządzanych.

Opcje **/Arch** odnoszą się do rozszerzeń zestawu instrukcji o następujących cechach:

- **Ia32** jest starszym 32-bitowym zestawem instrukcji x86 bez żadnych operacji wektorowych i przy użyciu x87 dla obliczeń zmiennoprzecinkowych.

- Funkcja **SSE** umożliwia obliczanie przy użyciu wektorów maksymalnie czterech wartości zmiennoprzecinkowych o pojedynczej precyzji. Dodano również odpowiednie skalarne instrukcje zmiennoprzecinkowe.

- **SSE2** umożliwia obliczanie przy użyciu wektorów 128-bitowych o pojedynczej precyzji, podwójnej precyzji i 1, 2, 4 lub 8-bajtowych wartości całkowitych. Dodano również instrukcje skalarne o podwójnej precyzji.

- **AVX** wprowadził alternatywne kodowanie instrukcji dla wektorów i zmiennoprzecinkowych instrukcji skalarnych, które umożliwiają wektorów 128 bitów lub 256 bitów, a zero — rozszerza wszystkie wyniki wektorów do pełnego rozmiaru wektora. (W przypadku starszej zgodności, instrukcje wektora stylu SSE zachowują wszystkie bity poza bitowym 127). Większość operacji zmiennoprzecinkowych jest przedłużona do 256 bitów.

- **AVX2** rozszerza większość operacji całkowitych na 256-bitowe wektory i umożliwia korzystanie z odpornych instrukcji typu "pomnóż-Add" (FMA).

- **AVX512** wprowadza inny formularz kodowania instrukcji, który umożliwia 512-bitowe wektory oraz niektóre inne funkcje opcjonalne. Dodano również instrukcje dotyczące dodatkowych operacji.

Optymalizator wybiera, kiedy i jak używać instrukcji wektorowych w zależności od tego, który **/Arch** jest określony. Skalarne obliczenia zmiennoprzecinkowe są wykonywane przy użyciu instrukcji SSE lub AVX, jeśli są dostępne. Niektóre konwencje wywoływania określają przekazywanie argumentów zmiennoprzecinkowych na stosie x87. w związku z tym kod może używać mieszanki instrukcji x87 i SSE/AVX dla obliczeń zmiennoprzecinkowych. Instrukcje wektora liczb całkowitych mogą być również używane dla niektórych operacji 64-bitowych liczb całkowitych, jeśli są dostępne.

Oprócz wektorów i zmiennoprzecinkowych instrukcji skalarnych każda opcja **/Arch** może także umożliwić użycie innych instrukcji innych niż wektorowe, które są skojarzone z tą opcją. Przykładem jest rodzina instrukcji CMOVcc, która po raz pierwszy pojawiła się na procesorach Intel Pentium Pro. Ponieważ instrukcje SSE zostały wprowadzone wraz z kolejnym procesorem Intel Pentium III, instrukcje CMOVcc można generować z wyjątkiem przypadków, gdy określono **/arch: ia32** .

Operacje zmiennoprzecinkowe są zwykle zaokrąglane do podwójnej precyzji (64-bitowe) w kodzie x87, ale można użyć `_controlfp`, aby zmodyfikować słowo kontrolne FP, włącznie z ustawieniem kontroli dokładności na rozszerzoną precyzję (80-bitową) lub pojedynczej precyzji (32-bit). Aby uzyskać więcej informacji, zobacz [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md). SSE i AVX mają oddzielne instrukcje o pojedynczej precyzji i podwójnej precyzji dla każdej operacji, więc nie istnieje odpowiednik kodu SSE/AVX. Może to zmienić sposób zaokrąglania wyników, gdy wynik operacji zmiennoprzecinkowej jest używany bezpośrednio do dalszej obliczeń zamiast przypisywania go do zmiennej użytkownika. Rozważ następujące źródła:

```cpp
r = f1 * f2 + d;  // Different results are possible on SSE/SSE2.
```

Z jawnym przypisaniem:

```cpp
t = f1 * f2;   // Do f1 * f2, round to the type of t.
r = t + d;     // This should produce the same overall result
               // whether x87 stack is used or SSE/SSE2 is used.
```

**/Arch** i [/QIfist](qifist-suppress-ftol.md) nie mogą być używane w tym samym jednostka kompilacji. Opcja **/QIfist** zmienia zachowanie zaokrąglania zmiennoprzecinkowego na konwersję liczb całkowitych. Domyślnym zachowaniem jest obcinanie (zaokrąglanie w kierunku zera), podczas gdy opcja **/QIfist** określa użycie trybu zaokrąglania środowiska zmiennoprzecinkowego. Ponieważ spowoduje to zmianę zachowania wszystkich konwersji zmiennoprzecinkowych na liczbę całkowitą, ta flaga jest przestarzała. Podczas kompilowania dla instrukcji SSE lub AVX można zaokrąglić wartość zmiennoprzecinkową do liczby całkowitej przy użyciu trybu zaokrąglania środowiska zmiennoprzecinkowego za pomocą wewnętrznej sekwencji funkcji:

```cpp
int convert_float_to_int(float x) {
    return _mm_cvtss_si32(_mm_set_ss(x));
}

int convert_double_to_int(double x) {
    return _mm_cvtsd_si32(_mm_set_sd(x));
}
```

Makra `_M_IX86_FP`, `__AVX__`, `__AVX2__`, `__AVX512F__`, `__AVX512CD__`, `__AVX512BW__`, `__AVX512DQ__` i `__AVX512VL__` wskazują, które, w przypadku użycia opcji kompilatora **/Arch** . Aby uzyskać więcej informacji, zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md). Opcja **/arch: AVX2** i makro `__AVX2__` zostały wprowadzone w Visual Studio 2013 Update 2 w wersji 12.0.34567.1. Ograniczona obsługa **/arch: AVX512** została dodana w programie visual Studio 2017 i rozwinięta w programie visual Studio 2019.

### <a name="to-set-this-compiler-option-for-avx-avx2-avx512-ia32-sse-or-sse2-in-visual-studio"></a>Aby ustawić tę opcję kompilatora dla AVX, AVX2, AVX512, IA32, SSE lub SSE2 w programie Visual Studio

1. Otwórz okno dialogowe **strony właściwości** dla projektu. Aby uzyskać więcej informacji, [Zobacz C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Właściwości konfiguracji**, **C/C++**  folder.

1. Wybierz stronę właściwości **generowanie kodu** .

1. Zmodyfikuj właściwość **Włącz rozszerzony zestaw instrukcji** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Zobacz także

[/arch (Minimalna architektura procesora CPU)](arch-minimum-cpu-architecture.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
