---
title: "-ERRORREPORT (zgłaszaj wewnętrzne błędy konsolidatora) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /ERRORREPORT
- VC.Project.VCLinkerTool.ErrorReporting
dev_langs: C++
helpviewer_keywords:
- /ERRORREPORT linker option
- ERRORREPORT linker option
- -ERRORREPORT linker option
ms.assetid: f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e6242457bb4da3e19700f5018b2a484bfa05630b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="errorreport-report-internal-linker-errors"></a>/ERRORREPORT (Zgłaszaj wewnętrzne błędy konsolidatora)
```  
/errorReport:[ none | prompt | queue | send ]  
```  
  
## <a name="remarks"></a>Uwagi  
 Pozwala zapewnić wewnętrznych kompilatora informacje o błędzie (ICE) bezpośrednio do firmy Microsoft.  
  
 Opcja **/errorreport: Send** próbuje automatyczne wysyłanie informacji o błędach do firmy Microsoft, ale sukces zależy od ustawień rejestru. Aby uzyskać więcej informacji na temat sposobu ustawiania odpowiednie wartości w rejestrze, zobacz [jak włączyć automatyczne raportowanie błędów w programie Visual Studio 2008 wiersza polecenia narzędzia](http://go.microsoft.com/fwlink/?LinkID=184695) w witrynie MSDN.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **właściwości konfiguracji** folderu.  
  
3.  Kliknij przycisk **konsolidatora** folderu.  
  
4.  Kliknij przycisk **zaawansowane** strony właściwości.  
  
5.  Modyfikowanie **raportowanie błędów**właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ErrorReporting%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [/ errorreport (zgłaszaj wewnętrzne błędy kompilatora)](../../build/reference/errorreport-report-internal-compiler-errors.md)   
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)