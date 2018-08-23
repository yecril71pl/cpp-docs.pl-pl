---
title: -ALLOWBIND (Zapobiegaj powiązaniu biblioteki DLL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.PreventDLLBinding
- /allowbind
dev_langs:
- C++
helpviewer_keywords:
- /ALLOWBIND linker option
- binding DLLs
- preventing DLL binding
- ALLOWBIND linker option
- -ALLOWBIND linker option
- DLLs [C++], preventing binding
ms.assetid: 30e37e24-12e4-407e-988a-39d357403598
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a0bff9ec6502aab5787c492a15e008bc29926163
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2018
ms.locfileid: "42465261"
---
# <a name="allowbind-prevent-dll-binding"></a>/ALLOWBIND (Zapobiegaj powiązaniu biblioteki DLL)
```  
/ALLOWBIND[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 /ALLOWBIND:no Ustawia bit w nagłówku biblioteki DLL, która wskazuje Bind.exe, że obraz nie może być powiązana. Nie ma Biblioteka DLL była związana, jeśli jego została podpisana cyfrowo (powiązanie unieważnia podpis).  
  
 Można edytować istniejącej biblioteki DLL dla funkcjonalność /ALLOWBIND [/ALLOWBIND](../../build/reference/allowbind.md) — opcja polecenia EDITBIN narzędzia.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń **właściwości konfiguracji**, **konsolidatora**i wybierz **wiersza polecenia**.  
  
3.  Wprowadź `/ALLOWBIND:NO` do **dodatkowe opcje**.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)   
 [BindImage — funkcja](/windows/desktop/api/imagehlp/nf-imagehlp-bindimage)   
 [BindImageEx — funkcja](/windows/desktop/api/imagehlp/nf-imagehlp-bindimageex)