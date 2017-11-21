---
title: "-DELAY (ustawienia opóźnienia importowania ładowania) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /delay
- VC.Project.VCLinkerTool.DelayNoBind
- VC.Project.VCLinkerTool.SupportUnloadOfDelayLoadedDLL
- VC.Project.VCLinkerTool.DelayUnload
dev_langs: C++
helpviewer_keywords:
- delayed loading of DLLs, /DELAY option
- DELAY linker option
- /DELAY linker option
- -DELAY linker option
ms.assetid: 9334b332-cc58-4dae-b10f-a4c75972d50c
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 86b076b8a3591ef75ad07cd47a525e67576317f6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="delay-delay-load-import-settings"></a>/DELAY (Ustawienia opóźnienia importowania ładowania)
```  
/DELAY:UNLOAD  
/DELAY:NOBIND  
```  
  
## <a name="remarks"></a>Uwagi  
 Formanty przełącznik/DELAY — opcja [opóźnienie załadowanie](../../build/reference/linker-support-for-delay-loaded-dlls.md) dll:  
  
-   Kwalifikator UNLOAD informuje funkcję pomocnicza ładowaną opóźnienia, aby wspierała jawne zwalnianie biblioteki dll. Tabelę adresów importu (IAT) jest resetowany do postaci oryginalnej unieważnia IAT wskaźników i powoduje ich zostaną zastąpione.  
  
     Jeśli nie wybierzesz ZWOLNIONY, wszelkie wywołanie [FUnloadDelayLoadedDLL](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md) zakończy się niepowodzeniem.  
  
-   Kwalifikator NOBIND informuje konsolidator, nie można dołączyć możliwego do powiązania IAT do obrazu końcowego. Wartość domyślna to tworzenie IAT powiązania dla bibliotek DLL załadowanych z opóźnieniem. Obraz wynikowy nie można powiązać statycznie. (Obrazów za pomocą powiązania IATs może być statycznie powiązany przed jej wykonaniem.) Zobacz [/POWIĄZAĆ](../../build/reference/bind.md).  
  
     Jeśli plik DLL, który jest powiązany, funkcja pomocnika zostanie podjęta próba wykorzystania powiązane informacje zamiast wywoływać metodę [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx) na wszystkich importów do którego istnieje odwołanie. Sygnatura czasowa lub preferowany adres nie odpowiadają załadowanej biblioteki dll, funkcja pomocnika przyjmie założenie, powiązania IAT jest nieaktualna i będzie kontynuowane tak, jakby powiązania IAT nie istnieje.  
  
     NOBIND powoduje, że program obrazu będzie większy, ale można skrócić czas biblioteki DLL ładowania. Jeśli planujesz nigdy nie można powiązać z biblioteką DLL, NOBIND uniemożliwi powiązania IAT generowany.  
  
 Aby określić bibliotek DLL w celu opóźnienia ładowania, użyj [/delayload](../../build/reference/delayload-delay-load-import.md) opcji.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać informacje, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji**, **konsolidatora**, a następnie wybierz **zaawansowane**.  
  
3.  Modyfikowanie **bibliotek DLL załadowanych opóźnienie** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)