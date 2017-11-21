---
title: "-ALIGN (wyrównanie sekcji) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.Alignment
- /align
dev_langs: C++
helpviewer_keywords:
- sections, specifying alignment
- ALIGN linker option
- /ALIGN linker option
- -ALIGN linker option
- section alignment
- sections
ms.assetid: f2f8ac24-e90e-4bea-8205-f2960a3b1740
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e620719d5a69c333a45664fba5967a740224d4d5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="align-section-alignment"></a>/ALIGN (Wyrównanie sekcji)
```  
/ALIGN[:number]  
```  
  
## <a name="remarks"></a>Uwagi  
 gdzie:  
  
 `number`  
 Wartość wyrównania.  
  
## <a name="remarks"></a>Uwagi  
 Opcja/align Określa wyrównanie każdej z sekcji w liniowej przestrzeni adresowej programu. `number` Argument w bajtach i musi być potęgą liczby dwa. Wartość domyślna to 4K (4096). Konsolidator wygeneruje ostrzeżenie, jeśli wyrównanie tworzy nieprawidłowy obraz.  
  
 Jeśli piszesz aplikację, takie jak sterownik urządzenia, należy nie należy zmodyfikować wyrównania.  
  
 Istnieje możliwość modyfikowania wyrównanie sekcji z parametrem Wyrównaj do [/SECTION](../../build/reference/section-specify-section-attributes.md) opcji.  
  
 Wartość wyrównania, określonym przez użytkownika nie może być mniejszy niż największa wyrównanie sekcji.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji do **dodatkowe opcje** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)