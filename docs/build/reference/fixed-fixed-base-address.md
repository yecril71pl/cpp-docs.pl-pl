---
title: -FIXED (stałe adresy podstawowe) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /fixed
- VC.Project.VCLinkerTool.FixedBaseAddress
dev_langs:
- C++
helpviewer_keywords:
- preferred base address for loading program
- /FIXED linker option
- -FIXED linker option
- FIXED linker option
ms.assetid: 929bba5e-b7d8-40ed-943e-056aa3710fc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08b1193b7cfe58aed45e4feec598a49227eafc87
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374164"
---
# <a name="fixed-fixed-base-address"></a>/FIXED (Stałe adresy podstawowe)
```  
/FIXED[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 Informuje system operacyjny, aby załadować program tylko na jego preferowany adres podstawowy. Preferowany adres podstawowy jest niedostępny, system operacyjny nie ładuje plik. Aby uzyskać więcej informacji, zobacz [/BASE (adres podstawowy)](../../build/reference/base-base-address.md).  
  
 / Fixed: no jest ustawieniem domyślnym dla biblioteki DLL, a Fixed jest domyślne ustawienie dla dowolnego typu projektu.  
  
 W przypadku Fixed łącze nie generuje sekcji relokacji w programie. W czasie wykonywania Jeśli system operacyjny nie może załadować program pod określonym adresem go generuje komunikat o błędzie i program nie zostanie załadowany.  
  
 Określ/Fixed: No, aby wygenerować sekcji relokacji w programie.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **konsolidatora** folderu.  
  
3.  Wybierz **wiersza polecenia** strony właściwości.  
  
4.  Wpisz nazwę opcji i ustawień **dodatkowe opcje** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)