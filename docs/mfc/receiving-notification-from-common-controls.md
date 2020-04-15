---
title: Odbieranie powiadomienia od formantów wspólnych
ms.date: 11/04/2016
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
ms.openlocfilehash: 9205facb5ec4e2491308020d9667a27ab8deb96b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371779"
---
# <a name="receiving-notification-from-common-controls"></a>Odbieranie powiadomienia od formantów wspólnych

Typowe formanty są okna podrzędne, które wysyłają komunikaty powiadomień do okna nadrzędnego, gdy zdarzenia, takie jak dane wejściowe od użytkownika, występują w formancie.

Aplikacja opiera się na tych komunikatów powiadomień, aby określić, jakie działania użytkownik chce go podjąć. Najczęściej formanty wysyłają wiadomości powiadomień jako WM_NOTIFY wiadomości. Formanty systemu Windows wysyłają większość wiadomości powiadomień jako WM_COMMAND wiadomości. [CWnd::OnNotify](../mfc/reference/cwnd-class.md#onnotify) jest program obsługi dla WM_NOTIFY wiadomości. Podobnie `CWnd::OnCommand`jak w `OnNotify` przypadku , implementacja `OnCmdMsg` wysyła komunikat powiadomienia do obsługi w mapach wiadomości. Wpis mapy wiadomości do obsługi powiadomień jest ON_NOTIFY. Aby uzyskać więcej informacji, zobacz [Uwaga techniczna 61: ON_NOTIFY i WM_NOTIFY Wiadomości](../mfc/tn061-on-notify-and-wm-notify-messages.md).

Alternatywnie klasa pochodna może obsługiwać własne komunikaty powiadomień za pomocą "odbicia wiadomości". Aby uzyskać więcej informacji, zobacz [Uwaga techniczna 62: Odbicie wiadomości dla formantów systemu Windows](../mfc/tn062-message-reflection-for-windows-controls.md).

## <a name="retrieving-the-cursor-position-in-a-notification-message"></a>Pobieranie pozycji kursora w wiadomości powiadomienia

Czasami warto określić bieżącą pozycję kursora, gdy niektóre komunikaty powiadomień są odbierane przez wspólny formant. Na przykład warto określić bieżącą lokalizację kursora, gdy wspólny formant odbiera komunikat powiadomienia NM_RCLICK.

Istnieje prosty sposób, aby to `CWnd::GetCurrentMessage`osiągnąć, dzwoniąc . Jednak ta metoda pobiera tylko położenie kursora w momencie wysłania wiadomości. Ponieważ kursor mógł zostać przeniesiony od wysłania wiadomości, należy wywołać, `CWnd::GetCursorPos` aby uzyskać bieżącą pozycję kursora.

> [!NOTE]
> `CWnd::GetCurrentMessage`powinien być wywoływany tylko w ramach obsługi wiadomości.

Dodaj następujący kod do treści programu obsługi komunikatów powiadomień (w tym przykładzie NM_RCLICK):

[!code-cpp[NVC_MFCControlLadenDialog#4](../mfc/codesnippet/cpp/receiving-notification-from-common-controls_1.cpp)]

W tym momencie lokalizacja kursora myszy `cursorPos` jest przechowywana w obiekcie.

## <a name="see-also"></a>Zobacz też

[Tworzenie i używanie kontrolek](../mfc/making-and-using-controls.md)<br/>
[Formanty](../mfc/controls-mfc.md)
