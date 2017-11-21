---
title: "Włączanie etykietek narzędzi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- initializing tool tips [MFC]
- enabling tool tips [MFC]
- tool tips [MFC], initializing
- tool tips [MFC], enabling
ms.assetid: 06b7c889-7722-4ce6-8b88-9efa50fe6369
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7c7e35dab6a94a01851b667ce4ab3dd58aa4bd8d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="enabling-tool-tips"></a>Włączanie etykietek narzędzi
Można włączyć narzędzie Porada obsługę formantów podrzędnych okna (np. formanty w formie widoku lub okno dialogowe).  
  
### <a name="to-enable-tool-tips-for-the-child-controls-of-a-window"></a>Aby włączyć etykietki narzędzi dla formantów podrzędnych okna  
  
1.  Wywołanie `EnableToolTips` okna, dla którego chcesz podać etykietek narzędzi.  
  
2.  Podaj ciąg dla każdego formantu w Twojej [powiadomienia TTN_NEEDTEXT](../mfc/handling-ttn-needtext-notification-for-tool-tips.md) programu obsługi. Procedura obsługi jest dostępna w mapie komunikatów okna zawierającego formantów podrzędnych (na przykład klasie widoku formularza). Ten program obsługi powinna wywołać funkcję, który identyfikuje formant i ustawia **pszText** na określanie tekstu używany przez formantem etykietki narzędzia.  
  
## <a name="see-also"></a>Zobacz też  
 [Etykietki narzędzi w systemie Windows niepochodzące od obiektu CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

