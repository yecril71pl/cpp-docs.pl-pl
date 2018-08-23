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
ms.openlocfilehash: a92e8d30d2c15ac07bc5a6ff3e6438da46438674
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597504"
---
# <a name="fu-name-forced-using-file"></a>/FU (Nazwij wymuszone pliki dyrektywy #using)
Opcję kompilatora, która służy jako alternatywę do przekazywania nazwę pliku do [# dyrektywa using](../../preprocessor/hash-using-directive-cpp.md) w kodzie źródłowym.  
  
## <a name="syntax"></a>Składnia  
  
```  
/FU file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Określa plik metadanych, aby odwołać się w tej kompilacji.  
  
## <a name="remarks"></a>Uwagi  
 Przełącznik /FU trwa tylko jedną nazwę pliku. Do określenia wielu plików, za pomocą /FU każdej z nich.  
  
 Jeśli używasz języka C + +/ CLI i odwołują się do metadanych do użycia [przyjaznych zestawów](../../dotnet/friend-assemblies-cpp.md) funkcji, nie można użyć **/FU**. Za pomocą musi odwoływać się metadanych w kodzie `#using`— wraz z `[as friend]` atrybutu. Przyjazne zestawy nie są obsługiwane w Visual C++ składnika rozszerzenia C + +/ CX.  
  
 Aby uzyskać informacje o tym, jak utworzyć zestaw lub moduł, aby uzyskać środowisko uruchomieniowe języka wspólnego (CLR), zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md). Aby uzyskać informacje dotyczące sposobu tworzenia w języku C + +/ CX, zobacz [Kompilowanie aplikacji i bibliotek](../../cppcx/building-apps-and-libraries-c-cx.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **C/C++** folderu.  
  
3.  Wybierz **zaawansowane** stronę właściwości.  
  
4.  Modyfikowanie **życie #using** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Plik wyjściowy (/ F) opcje](../../build/reference/output-file-f-options.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)