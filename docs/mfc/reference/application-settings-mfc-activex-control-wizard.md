---
title: Ustawienia aplikacji, kreator kontrolek ActiveX MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.appset
helpviewer_keywords:
- MFC ActiveX Control Wizard, application settings
ms.assetid: 48475194-cc63-467f-8499-f142269a4c1c
ms.openlocfilehash: 55f202ffabe945e55589ab1fc771a1757e23ca2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372473"
---
# <a name="application-settings-mfc-activex-control-wizard"></a>Ustawienia aplikacji, kreator kontrolek ActiveX MFC

Ta strona Kreatora sterowania MFC ActiveX służy do projektowania i dodawania podstawowych funkcji do nowego projektu MFC ActiveX. Te ustawienia dotyczą samej aplikacji, a nie do żadnej określonej funkcji lub elementu formantu.

- **Licencja w czasie wykonywania**

   Wybierz tę opcję, aby wygenerować plik licencji użytkownika do dystrybucji z formantem. Licencja jest plikiem *tekstowym, projname*.lic. Ten plik musi znajdować się w tym samym katalogu co biblioteka DLL formantu, aby umożliwić utworzenie wystąpienia formantu w środowisku czasu projektowania. Zwykle rozpowszechniasz ten plik za pomocą formantu, ale klienci nie rozpowszechniają go.

- **Generowanie plików pomocy**

   Wybierz tę opcję, aby wygenerować pliki pomocy i skonfigurować projekt, aby uwzględnić pomoc dla formantu. Domyślny projekt, utworzony bez tej opcji, generuje tylko **About** pole, które jest wyświetlane, gdy użytkownik kliknie prawym przyciskiem myszy formantu, używa F1 lub kliknie **Pomoc** w kontenerze formantu.

   > [!NOTE]
   > Sposób wyświetlania pomocy zależy od sposobu interakcji formantu z jego kontenerem. Jeśli dodasz pomoc z kontenerem, należy obsługiwać komunikaty między formantem a kontenerem, aby odpowiednio wyświetlić pomoc.

   Podczas generowania plików pomocy za pomocą kreatora projekt zawiera następujące elementy:

  - Plik .vcxproj zawiera kod do tworzenia i konfigurowania pliku pomocy podczas tworzenia projektu.

  - Plik *projnamePropPage*.cpp zawiera funkcję [SetHelpInfo](../../mfc/reference/colepropertypage-class.md#sethelpinfo) w konstruktorze.

  - Plik projname.hpj, jest plik projektu pomocy używany przez kompilator pomocy do tworzenia pliku pomocy formantu ActiveX. Plik .hpj jest plikiem tekstowym zawierającym informacje o tworzeniu pliku pomocy i ścieżki do dodatkowych plików (na przykład bitmapy) plik pomocy zawiera.

  - Projekt zawiera katalog HLP zawierający pliki bitmapowe pomocy projektu i plik tematu pomocy (*projname*.rtf). Ten plik tematu pomocy zawiera standardowe tematy pomocy dla typowych właściwości, zdarzeń i metod obsługiwanych przez wiele formantów ActiveX. Możesz edytować plik rtf, aby dodać lub usunąć określone tematy pomocy.

## <a name="see-also"></a>Zobacz też

[Kreator kontrolek ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[Nazwy kontrolek, kreator kontrolek ActiveX MFC](../../mfc/reference/control-names-mfc-activex-control-wizard.md)<br/>
[Ustawienia kontrolki, kreator kontrolek ActiveX MFC](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)
