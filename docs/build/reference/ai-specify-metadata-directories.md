---
title: "-AI (Określ katalogi metadanych) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.AdditionalUsingDirectories
- VC.Project.VCNMakeTool.AssemblySearchPath
- /AI
- VC.Project.VCCLWCECompilerTool.AdditionalUsingDirectories
dev_langs: C++
helpviewer_keywords:
- /AI compiler option [C++]
- AI compiler option [C++]
- -AI compiler option [C++]
ms.assetid: fb9c1846-504c-4a3b-bb39-c8696de32f6f
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4e2f6cb90cd86dfc572c23ef6fd0e5661b339774
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ai-specify-metadata-directories"></a>/AI (Określ katalogi metadanych)
Określa, że kompilator będzie wyszukiwania można rozpoznać odwołania do pliku przekazany do katalogu `#using` dyrektywy.  
  
## <a name="syntax"></a>Składnia  
  
```  
/AIdirectory  
```  
  
## <a name="arguments"></a>Argumenty  
 `directory`  
 Katalog lub ścieżka, w której kompilator będzie wyszukiwał.  
  
## <a name="remarks"></a>Uwagi  
 Można przekazać tylko jeden katalog do **/AI** wywołania. Określ jedną **/AI** opcji dla każdej ścieżki ma kompilatora do wyszukiwania. Na przykład, aby dodać do ścieżki wyszukiwania kompilatora dla C:\Project\Meta i C:\Common\Meta `#using` dyrektywy, Dodaj `/AI"C:\Project\Meta" /AI"C:\Common\Meta"` do wiersza polecenia kompilatora lub Dodaj każdy katalog do **dodatkowych #using katalogów** Właściwość w programie Visual Studio.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  W okienku nawigacji wybierz **właściwości konfiguracji**, **C/C++**, **ogólne**.  
  
3.  Modyfikowanie **dodatkowych #using katalogów** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalUsingDirectories%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
 [#using — dyrektywa](../../preprocessor/hash-using-directive-cpp.md)