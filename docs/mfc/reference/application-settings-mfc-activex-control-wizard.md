---
title: "Ustawienia aplikacji, Kreator formantów MFC ActiveX | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfc.ctl.appset
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX Control Wizard, application settings
ms.assetid: 48475194-cc63-467f-8499-f142269a4c1c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4b63507ba50f5f9d7dfb0fe5487e2758ced02cdd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="application-settings-mfc-activex-control-wizard"></a>Ustawienia aplikacji, kreator kontrolek ActiveX MFC
Użyj tej strony Kreator kontrolek ActiveX MFC do projektowania i dodać podstawowe funkcje do nowego projektu MFC ActiveX. Te ustawienia mają zastosowanie do aplikacji, a nie do określonych funkcji ani elementu formantu.  
  
 **Licencji środowiska wykonawczego**  
 Wybierz tę opcję, aby wygenerować plik licencji użytkownika do rozprowadzania z formantem. Licencja jest plikiem tekstowym *nazwa_projektu.nazwa_modułu.nazwa_procedury*.lic. Ten plik musi znajdować się w tym samym katalogu co DLL formantu umożliwiają wystąpienia formantu ma zostać utworzony w środowisku projektowania. Zazwyczaj rozpowszechnianie tego pliku z formantu, ale klienci nie przeprowadzaj dystrybucji.  
  
 **Generuj pliki pomocy**  
 Wybierz tę opcję, aby wygenerować pliki pomocy zastępczych i konfigurowanie projektu, aby uwzględnić pomoc dla formantu. Domyślny projekt utworzony bez tej opcji tylko generuje **o** polu wyświetlanym po kliknięciu prawym przyciskiem myszy przez użytkownika, formantu, używa F1 lub kliknięciu **pomocy** formantu kontenera.  
  
> [!NOTE]
>  Wyświetlanie pomocy zależy od tego, jak formantu współdziała z jego kontenera. Jeśli dołączysz pomocy z Twojej kontenera musi obsługiwać wiadomości między formantem a kontenera, aby prawidłowo wyświetlić Pomoc.  
  
 Podczas generowania plików pomocy za pomocą Kreatora projektu obejmuje następujące elementy:  
  
-   Plik .vcxproj zawiera kod, aby utworzyć i skonfigurować plik pomocy, podczas tworzenia projektu.  
  
-   Plik *projnamePropPage*zawiera plik .cpp [SetHelpInfo](../../mfc/reference/colepropertypage-class.md#sethelpinfo) funkcji w konstruktorze.  
  
-   Projname.hpj plik jest używany przez kompilator pomocy, aby utworzyć plik Pomocy formantu ActiveX pliku projektu pomocy. Plik .hpj jest plik tekstowy zawierający informacje na temat tworzenia pliku pomocy i ścieżki do pliku Pomocy znajdują się dodatkowe pliki (na przykład map bitowych).  
  
-   Projekt zawiera HLP katalog zawierający pliki map bitowych pomocy projektu i pliku tematu Pomocy (*nazwa_projektu.nazwa_modułu.nazwa_procedury*.rtf). Ten plik tematu Pomocy zawiera standardowe tematy pomocy dla wspólnych właściwości, zdarzeń i metod obsługiwanych przez wiele formantów ActiveX. Można edytować pliku RTF, aby dodać lub usunąć określonych tematów Pomocy.  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator kontrolek ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md)   
 [Nazwy formantów, Kreator kontrolek ActiveX MFC](../../mfc/reference/control-names-mfc-activex-control-wizard.md)   
 [Ustawienia kontrolki, kreator kontrolek ActiveX MFC](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)

