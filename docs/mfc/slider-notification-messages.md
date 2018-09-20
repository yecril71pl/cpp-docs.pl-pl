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
ms.openlocfilehash: 775ca98ff19266343631ff54bac16bebfff9e264
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399538"
---
# <a name="slider-notification-messages"></a>Komunikaty powiadomień suwaka

Kontrolki suwaka powiadamia okna nadrzędnego akcji użytkownika, wysyłając nadrzędnego WM_HSCROLL lub WM_VSCROLL wiadomości, w zależności od orientację przestrzenną kontrolki slider. Aby obsługiwać te komunikaty, należy dodać programy obsługi komunikatów WM_HSCROLL i WM_VSCROLL do okna nadrzędnego. [OnHScroll](../mfc/reference/cwnd-class.md#onhscroll) i [OnVScroll](../mfc/reference/cwnd-class.md#onvscroll) elementów członkowskich zostanie przekazany kod powiadomienia, położenie suwaka i wskaźnik [z CSliderCtrl](../mfc/reference/csliderctrl-class.md) obiektu. Należy zauważyć, że wskaźnik jest typu `CScrollBar *` mimo że wskazuje on `CSliderCtrl` obiektu. Może być konieczne rzutowanie typu ten wskaźnik, jeśli zachodzi potrzeba manipulowania kontrolki suwaka.

Zamiast używania przewijania powiadomień kody kreskowe, kontrolki suwaka Wyślij inny zestaw kodów powiadomień. Kontrolki suwaka wysyła kody powiadamiania TB_BOTTOM, TB_LINEDOWN, TB_LINEUP i TB_TOP tylko wtedy, gdy użytkownik wchodzi w interakcję z kontrolką suwaka za pomocą klawiatury. Komunikaty powiadomień TB_THUMBPOSITION i TB_THUMBTRACK są wysyłane tylko w sytuacji, gdy użytkownik korzysta z myszy. Kody powiadamiania TB_ENDTRACK TB_PAGEDOWN i TB_PAGEUP są wysyłane w obu przypadkach.

W poniższej tabeli wymieniono komunikaty powiadomień dotyczących kontrolki suwaka i zdarzenia (wirtualny kody klawiszy lub zdarzenia myszy), które powodują powiadomienia do wysłania. (Aby uzyskać listę standardowa wirtualnej kody klawiszy, zobacz Winuser.h).

|Komunikat z powiadomieniem|Zdarzenia będącego przyczyną powiadomień do wysłania|
|--------------------------|-------------------------------------------|
|TB_BOTTOM|VK_END|
|TB_ENDTRACK|WM_KEYUP (klucz, który jest wysyłany odpowiedni kod klawisza wirtualnego wydane użytkownika)|
|TB_LINEDOWN|VK_RIGHT lub VK_DOWN|
|TB_LINEUP|VK_LEFT lub VK_UP|
|TB_PAGEDOWN|VK_NEXT (użytkownik kliknął element kanału poniżej lub po prawej stronie suwaka)|
|TB_PAGEUP|VK_PRIOR (użytkownik kliknął element kanału powyżej lub po lewej stronie suwaka)|
|TB_THUMBPOSITION|WM_LBUTTONUP następującego komunikatu powiadomienia TB_THUMBTRACK|
|TB_THUMBTRACK|Przenoszenie suwaka (użytkownik przeciągnięciu suwaka)|
|TB_TOP|VK_HOME|

## <a name="see-also"></a>Zobacz też

[Korzystanie z CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

