---
title: Komunikaty powiadomień suwaka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CSliderCtrl class [MFC], notifications
- slider controls [MFC], notification messages
- messages, notification
- notifications [MFC], CSliderCtrl
ms.assetid: b9121104-3889-4a10-92bf-f3723f1af9d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c383458905d16dda935254e56a5aa9f56a153e83
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956164"
---
# <a name="slider-notification-messages"></a>Komunikaty powiadomień suwaka
Formantu suwaka powiadamia jej okna nadrzędnego akcje użytkownika, wysyłając nadrzędnego WM_HSCROLL lub WM_VSCROLL komunikaty, w zależności od Orientacja formantu suwaka. Aby obsługiwać te komunikaty, Dodaj programy obsługi komunikatów WM_HSCROLL i WM_VSCROLL do okna nadrzędnego. [OnHScroll](../mfc/reference/cwnd-class.md#onhscroll) i [OnVScroll](../mfc/reference/cwnd-class.md#onvscroll) funkcje Członkowskie zostanie przekazany kod powiadomienia, położenie suwaka i wskaźnika do [CSliderCtrl](../mfc/reference/csliderctrl-class.md) obiektu. Należy pamiętać, że wskaźnik jest typu `CScrollBar *` mimo że wskazuje `CSliderCtrl` obiektu. Konieczne może być rzutowanie typu ten wskaźnik, jeśli potrzebujesz do manipulowania suwaka.  
  
 Zamiast przy użyciu paska powiadomień kody przewijania, suwaków wysłać inny zestaw kodów powiadomień. Formant suwaka wysyła kody powiadamiania TB_BOTTOM, TB_LINEDOWN TB_LINEUP i TB_TOP tylko wtedy, gdy użytkownik wchodzi w interakcję z formantu suwaka za pomocą klawiatury. Komunikaty powiadomień TB_THUMBPOSITION i TB_THUMBTRACK są wysyłane tylko w przypadku, gdy użytkownik korzysta z myszą. Kody TB_ENDTRACK, TB_PAGEDOWN i TB_PAGEUP powiadomienia są wysyłane w obu przypadkach.  
  
 W poniższej tabeli wymieniono komunikaty powiadomień dotyczących formantu suwaka i zdarzenia (wirtualny kody lub zdarzenia myszy), które powodują powiadomień do wysłania. (Listę standardowych wirtualnego kodów klucza, zobacz Winuser.h).  
  
|Komunikat z powiadomieniem|Zdarzenia będącego przyczyną powiadomień do wysłania|  
|--------------------------|-------------------------------------------|  
|TB_BOTTOM|VK_END|  
|TB_ENDTRACK|WM_KEYUP (użytkownik wydane klucz, który wysłał odpowiedni kod klucza wirtualnego)|  
|TB_LINEDOWN|VK_RIGHT lub VK_DOWN|  
|TB_LINEUP|VK_LEFT lub VK_UP|  
|TB_PAGEDOWN|VK_NEXT (użytkownik kliknął kanału poniżej lub po prawej stronie suwaka)|  
|TB_PAGEUP|VK_PRIOR (użytkownik kliknął kanału powyżej lub po lewej stronie suwaka)|  
|TB_THUMBPOSITION|WM_LBUTTONUP następującego komunikatu powiadomienia TB_THUMBTRACK|  
|TB_THUMBTRACK|Przenoszenie suwaka (użytkownik przeciągnąć suwak)|  
|TB_TOP|VK_HOME|  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

