---
title: -NXCOMPAT (zgodny z zapobieganiem wykonywaniu danych) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /NXCOMPAT
dev_langs: C++
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.assetid: 5858e7ff-24d3-4ac3-9046-af2c9e220d9b
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d97b1b84ef6894e4ec161dbcecef47f6b676af23
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (Zgodny z zapobieganiem wykonywaniu danych)
Wskazuje, że plik wykonywalny w celu zachowania zgodności z funkcją zapobiegania wykonywaniu danych systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
/NXCOMPAT[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie **/NXCOMPAT** znajduje się na.  
  
 **: No** może służyć do jawnie określ plik wykonywalny jako niezgodne z zapobieganiem wykonywaniu danych.  
  
 Aby uzyskać więcej informacji na temat zapobiegania wykonywaniu danych zobacz następujące artykuły:  
  
-   [Szczegółowy opis funkcja Zapobieganie wykonywaniu danych (DEP)](http://go.microsoft.com/fwlink/?LinkID=157771) w witrynie Microsoft Help i pomocy technicznej  
  
-   [Zapobieganie wykonywaniu danych](http://go.microsoft.com/fwlink/?LinkID=157770) w witrynie MSDN w sieci Web  
  
-   [Zapobieganie wykonywaniu danych (z systemem Windows Embedded)](http://go.microsoft.com/fwlink/?LinkID=157768) w witrynie MSDN w sieci Web  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji w **dodatkowe opcje** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)