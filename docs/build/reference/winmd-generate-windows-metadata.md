---
title: -WINMD (Generuj metadane systemu Windows) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.VCLinkerTool.GenerateWindowsMetadata
dev_langs: C++
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 903ab6875457aa8c069c47a2be7f8ff1f5c884a9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="winmd-generate-windows-metadata"></a>/WINMD (generuj metadane systemu Windows)
Włącza generowanie pliku metadanych środowiska wykonawczego systemu Windows (.winmd).  
  
```  
/WINMD[:{NO|ONLY}]  
```  
  
## <a name="remarks"></a>Uwagi  
 / WINMD.  
 Ustawieniem domyślnym dla [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji. Konsolidator generuje zarówno pliku wykonywalnego binarnego, jak i plik metadanych winmd.  
  
 /WINMD:NO  
 Konsolidator generuje tylko binarny plik wykonywalny, ale nie jest plikiem winmd.  
  
 / WINMD: TYLKO  
 Konsolidator generuje plik winmd, ale nie binarnego pliku wykonywalnego.  
  
 Domyślnie, nazwa pliku wyjściowego ma postać `binaryname`winmd. Aby określić inną nazwę pliku, użyj [/WINMDFILE](../../build/reference/winmdfile-specify-winmd-file.md) opcji.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **konsolidatora** folderu.  
  
3.  Wybierz **metadanych systemu Windows** strony właściwości.  
  
4.  W **Generowanie metadanych systemu Windows** listy rozwijanej wybierz odpowiednią opcję.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)