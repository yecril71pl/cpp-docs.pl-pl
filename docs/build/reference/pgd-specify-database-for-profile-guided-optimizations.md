---
title: "-PGD (Określ bazę danych dla optymalizacji sterowanych profilem) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.ProfileGuidedDatabase
dev_langs:
- C++
helpviewer_keywords:
- -PGD linker option
- /PGD linker option
ms.assetid: 9f312498-493b-461f-886f-92652257e443
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cb61395d9f3b8c98e17e3683a7c3897b9315d78b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="pgd-specify-database-for-profile-guided-optimizations"></a>/PGD (Określ bazę danych dla optymalizacji sterowanych profilem)
/ PGD:`filename`  
  
## <a name="remarks"></a>Uwagi  
 gdzie:  
  
 `filename`  
 Określa nazwę pliku .pgd, który będzie używany do przechowywania informacji o uruchomiony program.  
  
## <a name="remarks"></a>Uwagi  
 Korzystając z [/LTCG:PGINSTRUMENT](../../build/reference/ltcg-link-time-code-generation.md), użyj /PGD, aby określić niestandardowy nazwę lub lokalizację pliku .pgd. Jeśli nie określisz /PGD nazwę pliku .pgd będzie taka sama jak nazwa pliku wyjściowego (.exe lub .dll) i zostaną utworzone w tym samym katalogu, z którego został wywołany łącza.  
  
 Korzystając z /LTCG:PGOPTIMIZE, należy użyć /PGD, aby określić nazwę pliku .pgd, który będzie używany do utworzenia zoptymalizowanego obrazu.  
  
 Aby uzyskać więcej informacji, zobacz [profilowana Optymalizacja](../../build/reference/profile-guided-optimizations.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzła.  
  
3.  Rozwiń węzeł **konsolidatora** węzła.  
  
4.  Wybierz **optymalizacji** strony właściwości.  
  
5.  Modyfikowanie **bazy danych profilu z przewodnikiem** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProfileGuidedDatabase%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)