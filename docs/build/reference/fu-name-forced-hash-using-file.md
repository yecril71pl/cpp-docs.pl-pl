---
title: '-FU (nazwij wymuszone #using) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.ForcedUsingFiles
- /FU
- VC.Project.VCNMakeTool.ForcedUsingAssemblies
dev_langs:
- C++
helpviewer_keywords:
- -FU compiler option [C++]
- FU compiler option [C++]
- /FU compiler option [C++]
ms.assetid: 698f8603-457f-435a-baff-5ac9243d6ca1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c9a27d8c689b198bde47047969d38cf14b41c46
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375678"
---
# <a name="fu-name-forced-using-file"></a>/FU (Nazwij wymuszone pliki dyrektywy #using)
Opcję kompilatora, która służy jako alternatywę do przekazywania nazwę pliku do [# dyrektywa using](../../preprocessor/hash-using-directive-cpp.md) w kodzie źródłowym.  
  
## <a name="syntax"></a>Składnia  
  
```  
/FU file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Określa plik metadanych do odwołania się w tej kompilacji.  
  
## <a name="remarks"></a>Uwagi  
 Przełącznik /FU przyjmuje tylko jedną nazwę pliku. Aby określić wiele plików, użyj /FU z każdej z nich.  
  
 Jeśli używasz [!INCLUDE[cppcli](../../build/reference/includes/cppcli_md.md)] i odwołują się do metadanych do użycia [przyjazne zestawy](../../dotnet/friend-assemblies-cpp.md) funkcji, nie można użyć **/FU**. Odwołanie do metadanych w kodzie za pomocą `#using`— wraz z `[as friend]` atrybutu. Przyjazne zestawy nie są obsługiwane w [!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] ([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]).  
  
 Aby uzyskać informacje o sposobie tworzenia zestawu lub modułu środowisko uruchomieniowe języka wspólnego (CLR), zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md). Aby uzyskać informacje o sposobie budowania [!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)], zobacz [tworzenia aplikacji i bibliotek](../../cppcx/building-apps-and-libraries-c-cx.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **C/C++** folderu.  
  
3.  Wybierz **zaawansowane** strony właściwości.  
  
4.  Modyfikowanie **życie #using** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Plik wyjściowy (/ F) opcje](../../build/reference/output-file-f-options.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)