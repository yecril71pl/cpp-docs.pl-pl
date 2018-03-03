---
title: "Komunikaty powiadomień suwaka | Dokumentacja firmy Microsoft"
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
- CSliderCtrl class [MFC], notifications
- slider controls [MFC], notification messages
- messages, notification
- notifications [MFC], CSliderCtrl
ms.assetid: b9121104-3889-4a10-92bf-f3723f1af9d0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3a4fc9e9065017e04b6375d1e5a8e336d4366755
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="slider-notification-messages"></a>Komunikaty powiadomień suwaka
Formantu suwaka powiadamia jej okna nadrzędnego akcje użytkownika, wysyłając nadrzędnego `WM_HSCROLL` lub `WM_VSCROLL` komunikaty, w zależności od Orientacja formantu suwaka. Aby obsługiwać te komunikaty, Dodaj obsługę `WM_HSCROLL` i `WM_VSCROLL` wiadomości do okna nadrzędnego. [OnHScroll](../mfc/reference/cwnd-class.md#onhscroll) i [OnVScroll](../mfc/reference/cwnd-class.md#onvscroll) funkcje Członkowskie zostanie przekazany kod powiadomienia, położenie suwaka i wskaźnika do [CSliderCtrl](../mfc/reference/csliderctrl-class.md) obiektu. Należy pamiętać, że wskaźnik jest typu **CScrollBar \***  mimo że wskazuje `CSliderCtrl` obiektu. Konieczne może być rzutowanie typu ten wskaźnik, jeśli potrzebujesz do manipulowania suwaka.  
  
 Zamiast przy użyciu paska powiadomień kody przewijania, suwaków wysłać inny zestaw kodów powiadomień. Wysyła formantu suwaka **TB_BOTTOM**, **TB_LINEDOWN**, **TB_LINEUP**, i **TB_TOP** powiadomień kodów tylko wtedy, gdy nastąpi interakcja użytkownika za pomocą formantu suwaka za pomocą klawiatury. **TB_THUMBPOSITION** i **TB_THUMBTRACK** komunikaty powiadomień są wysyłane tylko, gdy użytkownik korzysta z myszą. **TB_ENDTRACK**, **TB_PAGEDOWN**, i **TB_PAGEUP** kody powiadomienia są wysyłane w obu przypadkach.  
  
 W poniższej tabeli wymieniono komunikaty powiadomień dotyczących formantu suwaka i zdarzenia (wirtualny kody lub zdarzenia myszy), które powodują powiadomień do wysłania. (Listę standardowych wirtualnego kodów klucza, zobacz Winuser.h).  
  
|Komunikat z powiadomieniem|Zdarzenia będącego przyczyną powiadomień do wysłania|  
|--------------------------|-------------------------------------------|  
|**TB_BOTTOM**|**VK_END**|  
|**TB_ENDTRACK**|`WM_KEYUP`(użytkownik wydane klucz, który wysłał odpowiedni kod klucza wirtualnego)|  
|**TB_LINEDOWN**|**VK_RIGHT** lub **VK_DOWN**|  
|**TB_LINEUP**|**VK_LEFT** lub **VK_UP**|  
|**TB_PAGEDOWN**|**VK_NEXT** (użytkownik kliknął kanału poniżej lub po prawej stronie suwaka)|  
|**TB_PAGEUP**|**VK_PRIOR** (użytkownik kliknął kanału powyżej lub po lewej stronie suwaka)|  
|**TB_THUMBPOSITION**|`WM_LBUTTONUP`Po **TB_THUMBTRACK** komunikatu powiadomienia|  
|**TB_THUMBTRACK**|Przenoszenie suwaka (użytkownik przeciągnąć suwak)|  
|**TB_TOP**|**VK_HOME**|  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

