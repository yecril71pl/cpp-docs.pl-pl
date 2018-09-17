---
title: Ustawienia aplikacji, Kreator kontrolek ActiveX MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.ctl.appset
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX Control Wizard, application settings
ms.assetid: 48475194-cc63-467f-8499-f142269a4c1c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0ad19a4c9726378a54bd68173decd2469c17ec75
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708575"
---
# <a name="application-settings-mfc-activex-control-wizard"></a>Ustawienia aplikacji, kreator kontrolek ActiveX MFC
Użyj tej strony Kreator kontrolek ActiveX MFC do projektowania i dodawanie podstawowych funkcji do nowego projektu MFC ActiveX. Te ustawienia mają zastosowanie w samej aplikacji, a nie żadnych określonych funkcji lub elementu kontrolki.  
  
- **Licencja czasu wykonywania**

   Wybierz tę opcję, aby wygenerować plik licencji użytkowników do rozpowszechniania za pomocą kontrolki. Licencja jest plikiem tekstowym *projname*.lic. Ten plik musi być w tym samym katalogu co formantu biblioteki DLL, aby zezwolić na wystąpienie kontrolki, które zostały utworzone w środowisku czasu projektowania. Ten plik zazwyczaj rozpowszechniać za pomocą kontrolki, ale klienci nie rozpowszechniaj je.  
  
- **Generuj pliki pomocy**

   Wybierz tę opcję, aby wygenerować pliki pomocy przekształcone na wycinki i konfigurowanie projektu do uwzględnienia pomocy dla kontrolki. Domyślny projekt utworzony bez tej opcji, generuje tylko **o** pole, które jest wyświetlane, gdy użytkownik kliknie prawym przyciskiem myszy przycisk kontrolki, używa F1 lub kliknie **pomocy** kontrolki kontenera.  
  
   > [!NOTE]
   > Jak wyświetlić pomocy, zależy od tego, jak formant współdziała z jego kontenerem. Jeśli dołączysz pomocy za pomocą kontenera musi obsługiwać wiadomości między formantem i kontener umożliwiające wyświetlanie Pomocy odpowiednio.  
  
   Podczas generowania plików pomocy przy użyciu Kreatora projektu obejmuje następujące funkcje:  
  
   - .Vcxproj plik zawiera kod do tworzenia i konfigurowania pliku pomocy, gdy projekt jest kompilowany.  
  
   - Plik *projnamePropPage*zawiera plik .cpp [SetHelpInfo](../../mfc/reference/colepropertypage-class.md#sethelpinfo) funkcję w konstruktorze.  
  
   - Projname.hpj pliku, to pliku projektu pomocy, które są używane przez kompilatora plików pomocy, aby utworzyć plik Pomocy formantu ActiveX. Plik .hpj to plik tekstowy zawierający informacje na temat tworzenia pliku pomocy i ścieżki do dodatkowych plików (na przykład, mapy bitowe), które zawiera plik pomocy.  
  
   - Projekt zawiera katalog HLP ma zawierać pliki map bitowych pomocy projektu i pliku tematu Pomocy (*projname*RTF). Ten plik tematu Pomocy zawiera standardowe tematy pomocy dla wspólnych właściwości, zdarzeń i metod obsługiwanych przez wiele formantów ActiveX. Możesz edytować plik RTF do dodawania lub usuwania określonych tematów Pomocy.  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator kontrolek ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md)   
 [Nazwy kontrolek, Kreator kontrolek ActiveX MFC](../../mfc/reference/control-names-mfc-activex-control-wizard.md)   
 [Ustawienia kontrolki, kreator kontrolek ActiveX MFC](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)

