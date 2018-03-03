---
title: "Obsługa powiadomienia TTN_NEEDTEXT w przypadku etykietek narzędzi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TTN_NEEDTEXT
dev_langs:
- C++
helpviewer_keywords:
- TTN_NEEDTEXT message [MFC]
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 26a3b74ca0bc11b169e195599c5172b245cf0529
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="handling-ttnneedtext-notification-for-tool-tips"></a>Obsługa powiadomienia TTN_NEEDTEXT w przypadku etykietek narzędzi
W ramach [Włączanie etykietek narzędzi](../mfc/enabling-tool-tips.md), obsługi **TTN_NEEDTEXT** wiadomości, dodając następujący wpis do mapy komunikatów z oknem właściciela:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]  
  
 `memberFxn`  
 Funkcja członkowska wywoływana, gdy potrzebny jest tekst dla przycisku.  
  
 Należy pamiętać, że identyfikator etykietka narzędzia, która jest zawsze 0.  
  
 Deklarowanie funkcji obsługi w definicji klasy w następujący sposób:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#53](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_2.h)]  
  
 gdy kursywy parametry są:  
  
 `id`  
 Identyfikator formantu, który wysyłane powiadomienia. Nie używany. Identyfikator formantu jest pobierana z **NMHDR** struktury.  
  
 `pNMHDR`  
 Wskaźnik do [NMTTDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb760258) struktury. Ta struktura jest również omówione w dalszych [struktura TOOLTIPTEXT](../mfc/tooltiptext-structure.md).  
  
 `pResult`  
 Wskaźnik do kod wyniku można ustawić przed zwróceniem. **TTN_NEEDTEXT** programy obsługi można zignorować `pResult` parametru.  
  
 Na przykład obsługi powiadomień widoku formularza:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#54](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]  
  
 Wywołanie `EnableToolTips` (ten fragment z `OnInitDialog`):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#55](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Etykietki narzędzi w systemie Windows niepochodzące od obiektu CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

