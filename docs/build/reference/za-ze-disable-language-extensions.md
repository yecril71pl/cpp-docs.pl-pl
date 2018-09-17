---
title: -Za, - Ze (Wyłącz rozszerzenia językowe) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.DisableLanguageExtensions
- /za
- /ze
- VC.Project.VCCLCompilerTool.DisableLanguageExtensions
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d239b6153a2fc725c2add3eddb5fbaace406469
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712823"
---
# <a name="za-ze-disable-language-extensions"></a>/Za, /Ze (Wyłącz rozszerzenia językowe)

**/Za** kompilator generuje błąd dla konstrukcji języka, które nie są zgodne z ANSI C89 lub ISO C ++ 11. **/Ze** opcji kompilatora, która jest domyślnie włączona, umożliwia korzystanie z rozszerzeń firmy Microsoft.

## <a name="syntax"></a>Składnia

```
/Za
/Ze
```

## <a name="remarks"></a>Uwagi

> [!NOTE]
>  **/Ze** opcja jest przestarzały, ponieważ jego zachowanie jest domyślnie włączone. Zalecane jest użycie [/Zc (zgodność)](../../build/reference/zc-conformance.md) opcje kompilatora do kontrolowania funkcji rozszerzenia języka. Aby uzyskać listę opcji kompilatora przestarzałe zobacz **usunięte opcje kompilatora i uznane za przestarzałe** sekcji [opcje kompilatora wymienione według kategorii](../../build/reference/compiler-options-listed-by-category.md).

Kompilator języka Visual C++ oferuje pewną liczbę funkcji przekracza określoną w normach ANSI C89, ISO C99 lub ISO C++. Te funkcje są określane zbiorczo jako rozszerzenia Microsoft do C i C++. Te rozszerzenia są domyślnie dostępne i nie jest dostępna podczas **/Za** określono opcję. Aby uzyskać więcej informacji na temat określonych rozszerzeń, zobacz [Extensions firmy Microsoft do C i C++](../../build/reference/microsoft-extensions-to-c-and-cpp.md).

Firma Microsoft zaleca, wyłącz rozszerzenia językowe, określając **/Za** opcję, jeśli planujesz portu program do innych środowisk. Gdy **/Za** jest określony, kompilator traktuje rozszerzone słów kluczowych jako identyfikatorów proste firmy Microsoft, wyłącza rozszerzenia Microsoft i automatycznie definiuje `__STDC__` wstępnie zdefiniowane makro dla programów C.

Inne opcje kompilatora, używane z **/Za** mogą mieć wpływ na sposób kompilator zapewnia zgodność ze standardami.

Sposoby, aby określić ustawienia zachowania określonych zgodność standardy, można zobaczyć [/Zc](../../build/reference/zc-conformance.md) — opcja kompilatora.

Aby uzyskać więcej informacji na temat problemów ze zgodnością w języku Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. W okienku nawigacji wybierz **właściwości konfiguracji**, **C/C++**, **języka**.

1. Modyfikowanie **Wyłącz rozszerzenia języka** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (Zgodność)](../../build/reference/zc-conformance.md)
