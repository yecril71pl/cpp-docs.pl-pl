---
title: -MANIFESTFILE (nazwa pliku manifestu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ManifestFile
dev_langs:
- C++
helpviewer_keywords:
- MANIFESTFILE linker option
- -MANIFESTFILE linker option
- /MANIFESTFILE linker option
ms.assetid: befa5ab2-a9cf-4c9b-969a-e7b4a930f08d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b95337afc790436187c547bba108da2161b0738b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="manifestfile-name-manifest-file"></a>/MANIFESTFILE (Podaj nazwę pliku manifestu)
```  
/MANIFESTFILE:filename  
```  
  
## <a name="remarks"></a>Uwagi  
 / Opcja MANIFESTFILE pozwala zmienić domyślną nazwę pliku manifestu.  Nazwa domyślnego pliku manifestu to nazwa pliku z dołączonym ".manifest".  
  
 / MANIFESTFILE nie przyniesie efektu, jeśli nie utworzysz także łącza z [/MANIFEST](../../build/reference/manifest-create-side-by-side-assembly-manifest.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzła.  
  
3.  Rozwiń węzeł **konsolidatora** węzła.  
  
4.  Wybierz **plik manifestu** strony właściwości.  
  
5.  Modyfikowanie **plik manifestu** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ManifestFile%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)