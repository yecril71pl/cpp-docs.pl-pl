---
title: "-X (Ignoruj standardowe ścieżki dołączanych plików) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /x
- VC.Project.VCCLCompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLWCECompilerTool.OVERWRITEStandardIncludePath
dev_langs: C++
helpviewer_keywords:
- /X compiler option [C++]
- include files, ignore standard path
- -X compiler option [C++]
- include directories, ignore standard
- X compiler option
- Ignore Standard Include Paths compiler option
ms.assetid: 16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5ed251e1b937d14c42d105d98c2771ed0a2d6172
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="x-ignore-standard-include-paths"></a>/X (Ignoruj standardowe ścieżki dołączanych plików)
Zabezpiecza kompilator przed wyszukiwaniem dołączonych plików w katalogach określonych w zmiennych środowiskowych PATH lub INCLUDE.  
  
## <a name="syntax"></a>Składnia  
  
```  
/X  
```  
  
## <a name="remarks"></a>Uwagi  
 Można użyć tej opcji z [/I (dodatkowe katalogi dołączenia)](../../build/reference/i-additional-include-directories.md) (**/I**`directory`) opcja.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **preprocesora** strony właściwości.  
  
4.  Modyfikowanie **Ignoruj standardową ścieżkę obejmują** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.IgnoreStandardIncludePath%2A>.  
  
## <a name="example"></a>Przykład  
 W poniższym poleceniu `/X` informuje kompilator, aby zignorować lokalizacji określonej przez zmiennych środowiskowych PATH lub INCLUDE i `/I` Określa katalog, w którym znajdują się pliki dołączane:  
  
```  
CL /X /I \ALT\INCLUDE MAIN.C  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)