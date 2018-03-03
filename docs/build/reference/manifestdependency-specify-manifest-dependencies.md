---
title: "-MANIFESTDEPENDENCY (Określ zależności manifestu) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalManifestDependencies
dev_langs:
- C++
helpviewer_keywords:
- MANIFESTDEPENDENCY linker option
- /MANIFESTDEPENDENCY linker option
- -MANIFESTDEPENDENCY linker option
ms.assetid: e4b68313-33a2-4c3e-908e-ac2b9f7d6a73
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 01da83a57769dbe5b86c5bc2a73875231b769cdd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="manifestdependency-specify-manifest-dependencies"></a>/MANIFESTDEPENDENCY (Określ zależności manifestu)
```  
/MANIFESTDEPENDENCY:manifest_dependency  
```  
  
## <a name="remarks"></a>Uwagi  
 / Opcja MANIFESTDEPENDENCY pozwala określić atrybuty, które zostaną umieszczone w \<zależności > sekcji pliku manifestu.  
  
 Zobacz [/MANIFEST (Manifest zestawu Utwórz Side-by-Side)](../../build/reference/manifest-create-side-by-side-assembly-manifest.md) informacji na temat sposobu tworzenia pliku manifestu.  
  
 Aby uzyskać więcej informacji na temat \<zależności > sekcji pliku manifestu, zobacz [pliki konfiguracji wydawcy](http://msdn.microsoft.com/library/aa375682).  
  
 / MANIFESTDEPENDENCY informacje mogą być przekazywane do konsolidatora w jeden z dwóch sposobów:  
  
-   Bezpośrednio w wierszu polecenia (lub w pliku odpowiedzi) z /MANIFESTDEPENDENCY.  
  
-   Za pomocą [komentarz](../../preprocessor/comment-c-cpp.md) pragma.  
  
 W poniższym przykładzie przedstawiono komentarz /MANIFESTDEPENDENCY przekazywane przez pragma,  
  
```  
#pragma comment(linker, "\"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"")  
```  
  
 które powoduje następujący wpis w pliku manifestu:  
  
```  
<dependency>  
  <dependentAssembly>  
    <assemblyIdentity type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*' />  
  </dependentAssembly>  
</dependency>  
```  
  
 Tym samym komentarze /MANIFESTDEPENDENCY mogą być przekazywane w wierszu polecenia w następujący sposób:  
  
```  
"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"  
```  
  
 Konsolidator będzie zbierać /MANIFESTDEPENDENCY komentarze, usunąć zduplikowane wpisy, a następnie dodaj wynikowy ciąg XML do pliku manifestu.  Jeśli konsolidator znajdzie konfliktów wpisów, plik manifestu będzie uszkodzony i aplikacja nie będzie można uruchomić (wpis można dodać do dziennika zdarzeń, wskazujący źródło problemu).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzła.  
  
3.  Rozwiń węzeł **konsolidatora** węzła.  
  
4.  Wybierz **plik manifestu** strony właściwości.  
  
5.  Modyfikowanie **dodatkowe zależności manifestu** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalManifestDependencies%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)