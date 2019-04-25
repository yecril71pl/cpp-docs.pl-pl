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
ms.openlocfilehash: 1db1dbdba4829ccf939cdc4f07ccfefe2474a35d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315888"
---
# <a name="za-ze-disable-language-extensions"></a>/Za, /Ze (Wyłącz rozszerzenia językowe)

**/Za** — opcja kompilatora wyłącza i emituje błędów dla rozszerzenia Microsoft do C, które nie są zgodne z ANSI, C90 C89/ISO. Przestarzała **/Ze** — opcja kompilatora umożliwia korzystanie z rozszerzeń firmy Microsoft. Rozszerzenia Microsoft są domyślnie włączone.

## <a name="syntax"></a>Składnia

> **/Za**<br/>
> **/Ze**

## <a name="remarks"></a>Uwagi

> [!NOTE]
> Korzystanie z **/Za** podczas kompilowania kodu C++ nie jest zalecane. **/Ze** opcja jest przestarzały, ponieważ jego zachowanie jest domyślnie włączone. Aby uzyskać listę opcji kompilatora przestarzałe zobacz [opcje kompilatora usunięte i przestarzałe](compiler-options-listed-by-category.md#deprecated-and-removed-compiler-options).

Kompilator Microsoft C/C++ obsługuje kompilowanie kodu C na dwa sposoby:

- Kompilator używa trybu kompilacji C domyślnie, gdy plik źródłowy ma *.c* rozszerzenia, lub gdy [TP](tc-tp-tc-tp-specify-source-file-type.md) lub [TP](tc-tp-tc-tp-specify-source-file-type.md) określono opcję. Kompilator języka C jest kompilatora C89/C90, która domyślnie umożliwia korzystanie z rozszerzeń firmy Microsoft dla języka C. Aby uzyskać więcej informacji na temat określonych rozszerzeń, zobacz [Extensions firmy Microsoft do C i C++](microsoft-extensions-to-c-and-cpp.md). Gdy oba kompilacji C i **/Za** opcja jest określona, kompilator języka C, jest ściśle zgodny ze standardem C89/C90. Kompilator traktuje rozszerzone słów kluczowych jako identyfikatorów proste firmy Microsoft wyłącza rozszerzenia Microsoft i automatycznie definiuje [ \_ \_STDC\_ \_ ](../../preprocessor/predefined-macros.md) wstępnie zdefiniowane makra dla programów C.

- Kompilator może skompilować kod C w trybie kompilacji C++. To zachowanie jest ustawieniem domyślnym dla plików źródłowych, które nie mają *.c* rozszerzenia i kiedy [/Tp](tc-tp-tc-tp-specify-source-file-type.md) lub [/TP](tc-tp-tc-tp-specify-source-file-type.md) określono opcję. W trybie kompilacji C++ kompilator obsługuje te części, które zostały włączone do C++ standard standardów ISO C99 i C11. Prawie cały kod języka C jest również poprawny kod C++. Niewielka liczba słowa kluczowe języka C i konstrukcji kodu nie są prawidłowy kod języka C++ lub jest interpretowana inaczej w języku C++. Kompilator zachowuje się zgodnie ze standardem w tych przypadkach C++. W trybie kompilacji C++ **/Za** opcji może spowodować nieoczekiwane zachowanie i nie jest zalecane.

Inne opcje kompilatora może mieć wpływ na sposób kompilator zapewnia zgodność ze standardami. Aby poznać sposoby Określ określonych standardowych języków C i C++ zachowania ustawień, zobacz [/Zc](zc-conformance.md) — opcja kompilatora. Aby uzyskać dodatkowe ustawienia zgodności standard C++, zobacz [/ permissive-](permissive-standards-conformance.md) i [/STD](std-specify-language-standard-version.md) opcje kompilatora.

Aby uzyskać więcej informacji na temat problemów ze zgodnością w języku Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. W okienku nawigacji wybierz **właściwości konfiguracji** > **C/C++** > **języka**.

1. Modyfikowanie **Wyłącz rozszerzenia języka** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora](compiler-options.md)<br/>
[/Zc (Zgodność)](zc-conformance.md)<br/>
[/permissive- (Zgodność ze standardami)](permissive-standards-conformance.md)<br/>
[/std (Określ wersję standardu języka)](std-specify-language-standard-version.md)<br/>
