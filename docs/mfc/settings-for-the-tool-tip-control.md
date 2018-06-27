---
title: Ustawienia dla narzędzia formantu etykietki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tool tips [MFC], activating
- CToolTipCtrl class [MFC], settings
ms.assetid: ff8c5c46-2047-403a-bd98-ffec3d21ee3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 39de60d17dae5a6d7b2965350162117d049c29c8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951117"
---
# <a name="settings-for-the-tool-tip-control"></a>Ustawienia formantu etykietki narzędzia
Można ustawić formantem etykietki narzędzia ([CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)) być aktywne lub nieaktywne. Po ustawieniu go jako aktywne formantem etykietki narzędzia jest wyświetlany, gdy kursor znajduje się na to narzędzie. Po ustawieniu go jako nieaktywny formantem etykietki narzędzia nie ma, nawet jeśli kursor znajduje się na to narzędzie. Wywołanie [Aktywuj](../mfc/reference/ctooltipctrl-class.md#activate) aktywować lub dezaktywować formantem etykietki narzędzia.  
  
 Można ustawić aktywnego podpowiedzi do wyświetlenia etykietka narzędzia, gdy kursor znajduje się w narzędzia, czy okno właściciela formantem etykietki narzędzia jest aktywny lub nieaktywny, za pomocą stylu TTS_ALWAYSTIP. Jeśli nie używasz tego stylu, formantem etykietki narzędzia pojawia się, gdy właściciel okno jest aktywne, a nie jest nieaktywny.  
  
 Większość aplikacji zawierają paski narzędzi z narzędziami, które odpowiadają na polecenia menu. Tych narzędzi jest wygodną metodą formantem etykietki narzędzia do wyświetlania tego samego tekstu jako odpowiedniego elementu menu. System automatycznie usuwa handlowego "i" (&) akceleratora znaków z ciągów wszystkich przekazany do formantem etykietki narzędzia, chyba że formant ma styl TTS_NOPREFIX.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

