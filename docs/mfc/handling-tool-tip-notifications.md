---
title: "Obsługa powiadomień dotyczących etykietek narzędzi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- CToolBarCtrl class [MFC], handling notifications
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: ddb93b5f-2e4f-4537-8053-3453c86e2bbb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2b7668420b849dc08215a4fc309edf86e9171462
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="handling-tool-tip-notifications"></a>Obsługa powiadomień dotyczących etykietek narzędzi
Po określeniu `TBSTYLE_TOOLTIPS` styl, na pasku narzędzi tworzy i którymi zarządza formantem etykietki narzędzia. Etykietka narzędzia, która jest mała okno podręczne zawiera wiersz tekst opisujący przycisku paska narzędzi. Etykietka narzędzia, która jest ukryty, znajdujących się tylko użytkownik umieszcza kursor na przycisku paska narzędzi po pozostawia jej istnieje dla około połowy drugi. Etykietka narzędzia, która jest wyświetlana obok kursora.  
  
 Przed wyświetleniem etykietka narzędzia, **TTN_NEEDTEXT** komunikatu powiadomienia są wysyłane do okna nadrzędnego pasku narzędzi można pobrać tekst opisowy dla przycisku. Jeśli okno właściciela paska narzędzi jest `CFrameWnd` okno porad są wyświetlane bez żadnych dodatkowych nakładów, ponieważ narzędzie `CFrameWnd` ma domyślny program obsługi dla **TTN_NEEDTEXT** powiadomień. Jeśli okno właściciela paska narzędzi nie pochodzi od `CFrameWnd`, takie jak widok okna dialogowego pola lub formularz, należy dodać wpis do mapy komunikatów z oknem właściciela i podać obsługi powiadomień w mapie komunikatów. Zapis do mapy komunikatów z oknem właściciela jest następujący:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-tool-tip-notifications_1.cpp)]  
  
## <a name="remarks"></a>Uwagi  
 `memberFxn`  
 Funkcja członkowska wywoływana, gdy potrzebny jest tekst dla przycisku.  
  
 Należy pamiętać, że identyfikator etykietka narzędzia, która jest zawsze 0.  
  
 Oprócz **TTN_NEEDTEXT** powiadomienia formantem etykietki narzędzia można wysyłanie powiadomień do formantu toolbar:  
  
|powiadomienia|Znaczenie|  
|------------------|-------------|  
|**TTN_NEEDTEXTA**|Tekst w formacie ASCII (tylko system Windows 95) wymaga formantem etykietki narzędzia|  
|**TTN_NEEDTEXTW**|Tekst UNICODE (tylko system Windows NT) wymaga formantem etykietki narzędzia|  
|**TBN_HOTITEMCHANGE**|Wskazuje, że gorących (wyróżniony) element został zmieniony.|  
|**NM_RCLICK —**|Wskazuje, że użytkownik ma kliknął prawym przyciskiem myszy przycisk.|  
|**TBN_DRAGOUT**|Wskazuje, użytkownik kliknął element button i przeciągnąć kursor poza przycisk. Umożliwia aplikacji do wdrożenia przeciągania i upuszczania z przycisku paska narzędzi. Po odebraniu tego powiadomienia, aplikacja Rozpocznij przeciąganie i upuszczanie operacji.|  
|**TBN_DROPDOWN —**|Wskazuje, po kliknięciu przycisku, który używa **TBSTYLE_DROPDOWN** stylu.|  
|**TBN_GETOBJECT**|Wskazuje użytkownika przenieść wskaźnik na przycisku, który używa **TBSTYLE_DROPPABLE** stylu.|  
  
 Funkcję obsługi przykład i uzyskać więcej informacji o Włączanie etykietek narzędzi, zobacz [etykietki narzędzi](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

