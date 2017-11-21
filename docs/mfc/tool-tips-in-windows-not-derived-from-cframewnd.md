---
title: "Etykietki narzędzi w systemie Windows niepochodzące od obiektu CFrameWnd | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- enabling tool tips [MFC]
- TOOLTIPTEXT structure [MFC]
- Help [MFC], tool tips for controls
- TTN_NEEDTEXT message [MFC]
- controls [MFC], tool tips
- handler functions [MFC], tool tips
ms.assetid: cad5ef0f-02e3-4151-ad0d-3d42e6932b0e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d584f610a7cab58dc15a3f34859b317ae8c2571d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="tool-tips-in-windows-not-derived-from-cframewnd"></a>Etykietki narzędzi w systemie Windows niepochodzące od obiektu CFrameWnd
Rodzina ten artykuł obejmuje włączenie etykietki narzędzi dla formantów zawarte w oknie, który nie pochodzi od [cframewnd —](../mfc/reference/cframewnd-class.md). Artykuł [etykietki narzędzi pasków narzędzi](../mfc/toolbar-tool-tips.md) informacje na temat etykietki narzędzi dla formantów w `CFrameWnd`.  
  
 Tematy w tej rodzinie artykułu obejmują:  
  
-   [Włączanie etykietek narzędzi](../mfc/enabling-tool-tips.md)  
  
-   [Obsługa powiadomienia TTN_NEEDTEXT w przypadku etykietek narzędzi](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)  
  
-   [Struktura TOOLTIPTEXT](../mfc/tooltiptext-structure.md)  
  
 Etykietki narzędzi są automatycznie wyświetlane w przypadku przycisków, i inne formanty zawarte w oknie nadrzędnym pochodną `CFrameWnd`. Jest to spowodowane `CFrameWnd` ma domyślny program obsługi dla [TTN_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb760269) powiadomienie, które obsługuje **TTN_NEEDTEXT** powiadomienia z narzędzia Porada kontrolki skojarzone z formantami.  
  
 Jednak to domyślny program obsługi nie jest wywoływana, gdy **TTN_NEEDTEXT** powiadomienie jest wysyłane z formantem etykietki narzędzia, skojarzony z formantem w oknie, który nie jest `CFrameWnd`, takich jak kontrola na okno dialogowe lub widok formularza. Dlatego jest niezbędne do zapewnienia funkcji programu obsługi dla **TTN_NEEDTEXT** komunikatu powiadomienia w celu wyświetlenia etykietki narzędzi dla formantów podrzędnych.  
  
 Etykietki narzędzi domyślne podana dla systemu windows przez [CWnd::EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips) nie mają skojarzonych z nimi tekstu. Do pobierania tekstu podpowiedzi do wyświetlenia, **TTN_NEEDTEXT** powiadomienie jest wysyłane do okna nadrzędnego formantem etykietki narzędzia tuż przed wyświetleniem okna narzędzia poradę. Jeśli braku obsługi dla tej wiadomości, można przypisać wartości do **pszText** członkiem **TOOLTIPTEXT** struktury, nie będzie żadnych tekst wyświetlany na etykietka narzędzia.  
  
## <a name="see-also"></a>Zobacz też  
 [Etykietki narzędzi](../mfc/tool-tips.md)

