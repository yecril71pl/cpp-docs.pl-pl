---
title: -MANIFESTUAC (osadza informacje UAC w manifeście) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.UACUIAccess
- VC.Project.VCLinkerTool.UACExecutionLevel
- VC.Project.VCLinkerTool.EnableUAC
dev_langs:
- C++
helpviewer_keywords:
- /MANIFESTUAC linker option
- MANIFESTUAC linker option
- -MANIFESTUAC linker option
ms.assetid: 2d243c39-fa13-493c-b56f-d0d972a1603a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdfd872b43fbabdb14457ca54e6c4dfbe039313f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377277"
---
# <a name="manifestuac-embeds-uac-information-in-manifest"></a>/MANIFESTUAC (Osadza informacje UAC w manifeście)
Określa, czy informacje o kontroli konta użytkownika (UAC) jest osadzony w manifeście program.  
  
## <a name="syntax"></a>Składnia  
  
```  
/MANIFESTUAC  
/MANIFESTUAC:NO  
/MANIFESTUAC:fragment  
/MANIFESTUAC:level=_level  
/MANIFESTUAC:uiAccess=_uiAccess  
```  
  
#### <a name="parameters"></a>Parametry  
 `fragment`  
 Ciąg, który zawiera `level` i `uiAccess` wartości. Aby uzyskać więcej informacji zobacz sekcję uwag w dalszej części tego tematu.  
  
 `_level`  
 Jeden z *asInvoker*, *highestAvailable*, lub *requireAdministrator*. Wartość domyślna to asInvoker. Aby uzyskać więcej informacji zobacz sekcję uwag w dalszej części tego tematu.  
  
 `_uiAccess`  
 `true` Jeśli chcesz, aby aplikacja do obejścia poziomów ochrony interfejsu użytkownika i dysków danych wejściowych do systemu windows nowszej uprawnień na pulpit. w przeciwnym razie `false`. Domyślnie `false`. Ustaw `true` tylko dla aplikacji ułatwień dostępu interfejsu użytkownika.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli określisz wiele opcji /MANIFESTUAC w wierszu polecenia, pierwszeństwo ma ostatnią wprowadzona.  
  
 Dostępne są następujące opcje dla /MANIFESTUAC:level:  
  
-   `asInvoker`: Aplikacja będzie uruchamiana z takimi samymi uprawnieniami jak proces, który je zainicjował. Aplikacja może podniesiony do wyższego poziomu uprawnień, wybierając **Uruchom jako Administrator**.  
  
-   highestAvailable: aplikacja będzie uruchamiana z najwyższy poziom uprawnień, który może. Jeśli użytkownik uruchamia aplikację jest członkiem grupy Administratorzy, ta opcja jest taka sama jak requireAdministrator. Jeśli najwyższy poziom uprawnień dostępne jest wyższy niż poziom procesu otwierania, system wyświetli monit o podanie poświadczeń.  
  
-   requireAdministrator: aplikacja będzie uruchamiana z uprawnieniami administratora. Użytkownik, który uruchamia aplikację musi być członkiem grupy Administratorzy. Jeśli proces otwierania nie jest uruchomiony z uprawnieniami administracyjnymi, system wyświetli monit o podanie poświadczeń.  
  
 Można określić wartości poziomu i uiAccess w jednym kroku przy użyciu opcji /MANIFESTUAC:fragment. Fragment, musi być w następującym formacie:  
  
```  
"level=[ asInvoker | highestAvailable | requireAdministrator ] uiAccess=[ true | false ]"  
```  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzła.  
  
3.  Rozwiń węzeł **konsolidatora** węzła.  
  
4.  Wybierz **plik manifestu** strony właściwości.  
  
5.  Modyfikowanie **włączyć (Kontrola konta)**, **poziom wykonywania UAC**, i **ochrona Interfejsu użytkownika obejścia kontroli konta użytkownika** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableUAC%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACExecutionLevel%2A>, i <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACUIAccess%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)