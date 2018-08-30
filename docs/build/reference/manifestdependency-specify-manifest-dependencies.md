---
title: -MANIFESTDEPENDENCY (Określ zależności manifestu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalManifestDependencies
dev_langs:
- C++
helpviewer_keywords:
- MANIFESTDEPENDENCY linker option
- /MANIFESTDEPENDENCY linker option
- -MANIFESTDEPENDENCY linker option
ms.assetid: e4b68313-33a2-4c3e-908e-ac2b9f7d6a73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d486047b708e0c3412aa63e0a0b026a2a4204f71
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213902"
---
# <a name="manifestdependency-specify-manifest-dependencies"></a>/MANIFESTDEPENDENCY (Określ zależności manifestu)
```  
/MANIFESTDEPENDENCY:manifest_dependency  
```  
  
## <a name="remarks"></a>Uwagi  
 / MANIFESTDEPENDENCY pozwala określić atrybuty, które zostaną umieszczone w \<zależności > sekcji w pliku manifestu.  
  
 Zobacz [/MANIFEST (Side-by-Side tworzenie manifestu dla aplikacji)](../../build/reference/manifest-create-side-by-side-assembly-manifest.md) informacji na temat tworzenia pliku manifestu.  
  
 Aby uzyskać więcej informacji na temat \<zależności > sekcji pliku manifestu, zobacz [pliki konfiguracyjne wydawcy](/windows/desktop/SbsCs/publisher-configuration-files).  
  
 / MANIFESTDEPENDENCY informacje mogą być przekazywane do konsolidatora w jeden z dwóch sposobów:  
  
-   Bezpośrednio w wierszu polecenia (lub w pliku odpowiedzi) przy użyciu /MANIFESTDEPENDENCY.  
  
-   Za pomocą [komentarz](../../preprocessor/comment-c-cpp.md) pragmy.  
  
 W poniższym przykładzie przedstawiono komentarz /MANIFESTDEPENDENCY przekazywane przez dyrektywę,  
  
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
  
 Konsolidator zbierania /MANIFESTDEPENDENCY komentarzy, wyeliminować zduplikowane wpisy i następnie dodać wynikowy ciąg XML do pliku manifestu.  Jeśli konsolidator wykryje wpisy powodujące konflikt, plik manifestu zostanie uszkodzona, a aplikacja zakończy się niepowodzeniem (wpis mogą być dodawane do dziennika zdarzeń, wskazujący źródła błędów).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń **właściwości konfiguracji** węzła.  
  
3.  Rozwiń **konsolidatora** węzła.  
  
4.  Wybierz **pliku manifestu** stronę właściwości.  
  
5.  Modyfikowanie **dodatkowe zależności manifestu** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalManifestDependencies%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)