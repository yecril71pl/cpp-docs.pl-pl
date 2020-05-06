---
title: /Za, /Ze (Wyłącz rozszerzenia językowe)
ms.date: 02/19/2019
f1_keywords:
- VC.Project.VCCLWCECompilerTool.DisableLanguageExtensions
- /za
- /ze
- VC.Project.VCCLCompilerTool.DisableLanguageExtensions
helpviewer_keywords:
- -Za compiler option [C++]
- Za compiler option [C++]
- language extensions, disabling in compiler
- -Ze compiler option [C++]
- language extensions
- enable language extensions
- /Za compiler option [C++]
- /Ze compiler option [C++]
- Disable Language Extensions compiler option
- Ze compiler option [C++]
ms.assetid: 65e49258-7161-4289-a176-7c5c0656b1a2
ms.openlocfilehash: 9a2584591f6ca22d6767a5c447ffb72bea0a78ea
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825878"
---
# <a name="za-ze-disable-language-extensions"></a>/Za, /Ze (Wyłącz rozszerzenia językowe)

Opcja kompilatora **/za** wyłącza i emituje błędy dla rozszerzeń Microsoft do języka C, które nie są zgodne ze standardem ANSI C89/ISO C90. Przestarzała opcja kompilatora **/ze** umożliwia korzystanie z rozszerzeń firmy Microsoft. Rozszerzenia Microsoft są domyślnie włączone.

## <a name="syntax"></a>Składnia

> **/Za**\
> **/Ze**

## <a name="remarks"></a>Uwagi

> [!NOTE]
> Użycie **/za** podczas kompilowania kodu w języku C++ nie jest zalecane. Opcja **/ze** jest przestarzała, ponieważ jej zachowanie jest domyślnie włączone. Aby zapoznać się z listą przestarzałych opcji kompilatora, zobacz [Opcje kompilatora przestarzałe i usunięte](compiler-options-listed-by-category.md#deprecated-and-removed-compiler-options).

Kompilator języka Microsoft C/C++ obsługuje kompilację kodu języka C na dwa sposoby:

- Kompilator domyślnie używa trybu kompilacji C, gdy plik źródłowy ma rozszerzenie *c* lub jeśli określono opcję [/TC](tc-tp-tc-tp-specify-source-file-type.md) lub [/TC](tc-tp-tc-tp-specify-source-file-type.md) . Kompilator języka C to kompilator C89/C90, który domyślnie włącza rozszerzenia Microsoft do języka C. Aby uzyskać więcej informacji na temat określonych rozszerzeń, zobacz [Microsoft Extensions to C i C++](microsoft-extensions-to-c-and-cpp.md). Gdy określono zarówno kompilację języka C, jak i opcję **/za** , kompilator języka c jest zgodny ze standardem C89/C90. Kompilator traktuje rozszerzone słowa kluczowe Microsoft jako proste identyfikatory, wyłącza inne rozszerzenia Microsoft i automatycznie definiuje [ \_ \_\_ ](../../preprocessor/predefined-macros.md) wstępnie zdefiniowane makro STDC dla programów C.

- Kompilator może kompilować kod C w trybie kompilacji języka C++. To zachowanie jest domyślne dla plików źródłowych, które nie mają rozszerzenia *. c* , i gdy jest określona opcja [/TP](tc-tp-tc-tp-specify-source-file-type.md) lub [/TP](tc-tp-tc-tp-specify-source-file-type.md) . W trybie kompilacji C++ kompilator obsługuje te części standardów ISO C99 i C11, które zostały włączone do standardu C++. Prawie cały kod C jest również prawidłowym kodem języka C++. Niewielka liczba słów kluczowych C i konstrukcji kodu nie jest prawidłowym kodem C++ lub są interpretowane inaczej w języku C++. Kompilator zachowuje się zgodnie ze standardem C++ w takich przypadkach. W trybie kompilacji C++ opcja **/za** może spowodować nieoczekiwane zachowanie i nie jest zalecana.

Inne opcje kompilatora mogą mieć wpływ na sposób, w jaki kompilator zapewnia zgodność ze standardami. Aby uzyskać informacje na temat określania konkretnych ustawień zachowania standardowego C i C++, zobacz [/Zc](zc-conformance.md) — opcja kompilatora. Aby uzyskać dodatkowe ustawienia zgodności standardowego języka C++, zobacz Opcje kompilatora [/permissive-](permissive-standards-conformance.md) i [/STD](std-specify-language-standard-version.md) .

Aby uzyskać więcej informacji na temat problemów ze zgodnością Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. W okienku nawigacji wybierz pozycję **Właściwości** > konfiguracji**Język****C/C++** > .

1. Zmodyfikuj właściwość **Wyłącz rozszerzenia językowe** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora](compiler-options.md)<br/>
[/Zc (Zgodność)](zc-conformance.md)<br/>
[/permissive- (Zgodność ze standardami)](permissive-standards-conformance.md)<br/>
[/std (Określ wersję standardu języka)](std-specify-language-standard-version.md)<br/>
