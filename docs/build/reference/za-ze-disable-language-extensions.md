---
title: -Za-, - Ze (Wyłącz rozszerzenia językowe) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 2949a3d60af6d9058f02d12aac1fd86dead5affa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="za-ze-disable-language-extensions"></a>/Za, /Ze (Wyłącz rozszerzenia językowe)
**/Za** — opcja kompilatora emituje błąd dotyczące konstrukcji języka, które nie są zgodne z ANSI C89 lub ISO C ++ 11. **/Ze** opcję kompilatora, która jest domyślnie włączona, umożliwia korzystanie z rozszerzeń firmy Microsoft.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Za  
/Ze  
```  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  **/Ze** opcji jest przestarzały, ponieważ jego zachowanie jest domyślnie włączone. Zalecane jest użycie [/Zc (zgodność)](../../build/reference/zc-conformance.md) — opcje kompilatora do kontrolowania funkcji rozszerzenia języka. Listę opcji kompilatora przestarzałe, zobacz **uznane za przestarzałe i usunąć — opcje kompilatora** sekcji [kompilatora opcje rozbiciu na kategorie](../../build/reference/compiler-options-listed-by-category.md).  
  
 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] Kompilatora oferuje wiele funkcji poza tymi, które określono w standardach ANSI C89, ISO C99 lub ISO C++. Te funkcje są nazywane zbiorczo rozszerzenia Microsoft do C i C++. Te rozszerzenia są domyślnie dostępne i nie będzie dostępny podczas **/Za** określono opcję. Aby uzyskać więcej informacji na temat określonych rozszerzeń, zobacz [Extensions firmy Microsoft do C i C++](../../build/reference/microsoft-extensions-to-c-and-cpp.md).  
  
 Firma Microsoft zaleca, wyłącz rozszerzenia językowe, określając **/Za** opcję, jeśli planujesz portu programu do innych środowisk. Gdy **/Za** określono kompilator traktuje rozszerzone słowa kluczowe jako proste identyfikatory firmy Microsoft, wyłącza rozszerzenia Microsoft i automatycznie definiuje `__STDC__` wstępnie zdefiniowanego makra dla programów C.  
  
 Inne opcje kompilatora używane z **/Za** mogą mieć wpływ na sposób kompilator zapewnia zgodność standardów. Na przykład **/Za** i [/fp (określenie zachowania Floating-Point)](../../build/reference/fp-specify-floating-point-behavior.md) może spowodować typ zmiennoprzecinkowy zachowanie podwyższania poziomu, które nie jest zgodna z ISO C99 lub C ++ 11 standardów.  
  
 Dla metody Określ ustawienia zachowania określonych zgodność standardy, zobacz [/Zc](../../build/reference/zc-conformance.md) — opcja kompilatora.  
  
 Aby uzyskać więcej informacji dotyczących problemów zgodność z [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)], zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  W okienku nawigacji wybierz **właściwości konfiguracji**, **C/C++**, **języka**.  
  
3.  Modyfikowanie **Wyłącz rozszerzenia językowe** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [/Zc (Zgodność)](../../build/reference/zc-conformance.md)