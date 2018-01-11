---
title: "Ustawienia dla narzędzia formantu etykietki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- tool tips [MFC], activating
- CToolTipCtrl class [MFC], settings
ms.assetid: ff8c5c46-2047-403a-bd98-ffec3d21ee3a
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 406e35b6ab694ca972d4cd6add0dcca7586e5005
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="settings-for-the-tool-tip-control"></a>Ustawienia formantu etykietki narzędzia
Można ustawić formantem etykietki narzędzia ([CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)) być aktywne lub nieaktywne. Po ustawieniu go jako aktywne formantem etykietki narzędzia jest wyświetlany, gdy kursor znajduje się na to narzędzie. Po ustawieniu go jako nieaktywny formantem etykietki narzędzia nie ma, nawet jeśli kursor znajduje się na to narzędzie. Wywołanie [Aktywuj](../mfc/reference/ctooltipctrl-class.md#activate) aktywować lub dezaktywować formantem etykietki narzędzia.  
  
 Można ustawić aktywnego etykietka narzędzia, która wyświetlić etykietka narzędzia, gdy kursor znajduje się w narzędzia, czy okno właściciela formantem etykietki narzędzia jest aktywny lub nieaktywny, za pomocą **TTS_ALWAYSTIP** stylu. Jeśli nie używasz tego stylu, formantem etykietki narzędzia pojawia się, gdy właściciel okno jest aktywne, a nie jest nieaktywny.  
  
 Większość aplikacji zawierają paski narzędzi z narzędziami, które odpowiadają na polecenia menu. Tych narzędzi jest wygodną metodą formantem etykietki narzędzia do wyświetlania tego samego tekstu jako odpowiedniego elementu menu. System automatycznie usuwa znaków ampersand (&) akceleratora z wszystkich ciągów przekazana do formantem etykietki narzędzia, chyba że formant ma **TTS_NOPREFIX** stylu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

