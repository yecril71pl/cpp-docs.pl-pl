---
title: Odbieranie powiadomienia od formantów wspólnych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- ON_NOTIFY
- WM_NOTIFY
dev_langs:
- C++
helpviewer_keywords:
- OnNotify method [MFC]
- common controls [MFC], notifications
- ON_NOTIFY macro [MFC]
- controls [MFC], notifications
- receiving notifications from common controls
- notifications [MFC], common controls
- Windows common controls [MFC], notifications
- WM_NOTIFY message
ms.assetid: 50194592-d60d-44d0-8ab3-338a2a2c63e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 30e89c8d25d78477ed98bae0fd06a704e32d3906
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="receiving-notification-from-common-controls"></a>Odbieranie powiadomienia od formantów wspólnych
Formanty standardowe są okno podrzędne, które wysyłać powiadomienia do nadrzędnego okna w przypadku wystąpienia zdarzenia, takie jak dane wejściowe użytkownika w formancie.  
  
 Te komunikaty powiadomień, aby określić, jaką akcję użytkownik będzie chciał podjęcia zależy od aplikacji. Najbardziej typowe kontrolki wysyłać powiadomienia jako **WM_NOTIFY** wiadomości. Formanty systemu Windows wysyłać większości powiadomienia jako **WM_COMMAND** wiadomości. [CWnd::OnNotify](../mfc/reference/cwnd-class.md#onnotify) obsługi dla **WM_NOTIFY** wiadomości. Jak `CWnd::OnCommand`, implementacja `OnNotify` wysyła powiadomienie do `OnCmdMsg` obsługi w mapy komunikatów. Obsługa powiadomień dotyczących wpis mapy wiadomości jest `ON_NOTIFY`. Aby uzyskać więcej informacji, zobacz [techniczne 61 Uwaga: komunikaty ON_NOTIFY i WM_NOTIFY](../mfc/tn061-on-notify-and-wm-notify-messages.md).  
  
 Alternatywnie Klasa pochodna może obsługiwać własny komunikatów powiadomień za pomocą "odbicie wiadomości." Aby uzyskać więcej informacji, zobacz [techniczne 62 Uwaga: odbicie komunikatu dla formantów systemu Windows](../mfc/tn062-message-reflection-for-windows-controls.md).  
  
## <a name="retrieving-the-cursor-position-in-a-notification-message"></a>Pobieranie bieżącej pozycji kursora w komunikacie powiadomienia  
 Czasem jest przydatne do określenia bieżącej pozycji kursora, gdy niektóre komunikaty powiadomień są odbierane przez formantu wspólnego. Na przykład będą przydatne do określenia bieżącej lokalizacji kursora, gdy odbiera formantu wspólnego **nm_rclick —** wiadomość z powiadomieniem.  
  
 Brak prosty sposób, w tym celu przez wywołanie metody `CWnd::GetCurrentMessage`. Ta metoda pobiera jednak tylko bieżącej pozycji kursora w momencie wiadomość została wysłana. Ponieważ kursor został przeniesiony, ponieważ komunikat został wysłany, należy wywołać **CWnd::GetCursorPos** można uzyskać w bieżącej pozycji kursora.  
  
> [!NOTE]
>  `CWnd::GetCurrentMessage` należy wywoływać tylko w ramach obsługi wiadomości.  
  
 Dodaj następujący kod do treści funkcji obsługi komunikatów powiadomień (w tym przykładzie **nm_rclick —**):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#4](../mfc/codesnippet/cpp/receiving-notification-from-common-controls_1.cpp)]  
  
 W tym momencie przechowywanego w lokalizacji kursora myszy `cursorPos` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie i używanie formantów](../mfc/making-and-using-controls.md)   
 [Kontrolki](../mfc/controls-mfc.md)

