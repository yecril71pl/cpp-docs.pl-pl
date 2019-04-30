---
title: Odbieranie powiadomienia od formantów wspólnych
ms.date: 11/04/2016
f1_keywords:
- ON_NOTIFY
- WM_NOTIFY
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
ms.openlocfilehash: fb923374866aa8348f9b895c9b97915817564883
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399866"
---
# <a name="receiving-notification-from-common-controls"></a>Odbieranie powiadomienia od formantów wspólnych

Formanty standardowe są okien podrzędnych, które wysyłać powiadomienia do okna nadrzędnego po wystąpieniu zdarzenia, takie jak dane wejściowe użytkownika w kontrolce.

Aplikacja korzysta z tych komunikatów powiadomień w celu ustalenia, jakie działania użytkownik chce go, aby pobierał. Najczęstsze formanty wysyłać powiadomienia jako komunikaty WM_NOTIFY. Formanty Windows wysłać komunikaty powiadomień dotyczących większości jako wm_command — komunikaty. [CWnd::OnNotify](../mfc/reference/cwnd-class.md#onnotify) jest obsługa wm_notify — komunikat. Podobnie jak w przypadku `CWnd::OnCommand`, implementacja `OnNotify` wysyła powiadomienie do `OnCmdMsg` obsługi w mapy komunikatów. Obsługa powiadomień dotyczących wpis mapy komunikatów jest ON_NOTIFY. Aby uzyskać więcej informacji, zobacz [techniczne 61 Uwaga: Komunikaty ON_NOTIFY i Wm_notify](../mfc/tn061-on-notify-and-wm-notify-messages.md).

Alternatywnie klasy pochodnej może obsługiwać własny powiadomienia za pomocą "odbicie komunikatu". Aby uzyskać więcej informacji, zobacz [techniczne 62 Uwaga: Komunikat odbicie dla formantów Windows](../mfc/tn062-message-reflection-for-windows-controls.md).

## <a name="retrieving-the-cursor-position-in-a-notification-message"></a>Pobieranie bieżącej pozycji kursora w komunikat z powiadomieniem

Czasami jest to przydatne do określenia bieżącej pozycji kursora w przypadku, gdy niektóre komunikaty powiadomień są odbierane przez wspólnej kontroli. Na przykład może być przydatne do określenia bieżąca lokalizacja kursora, gdy formantu typowego otrzymuje komunikat z powiadomieniem nm_rclick —.

Brak najprościej można to zrobić, wywołując `CWnd::GetCurrentMessage`. Ta metoda pobiera jednak tylko pozycji kursora w czasie, który została wysłana wiadomość. Ponieważ kursor mogło zostać przeniesione, ponieważ została wysłana wiadomość, należy wywołać `CWnd::GetCursorPos` uzyskać aktualną pozycją kursora.

> [!NOTE]
>  `CWnd::GetCurrentMessage` powinna być wywoływana tylko w ramach programu obsługi komunikatów.

Dodaj następujący kod do treści program obsługi komunikatów powiadomień (w tym przykładzie nm_rclick —):

[!code-cpp[NVC_MFCControlLadenDialog#4](../mfc/codesnippet/cpp/receiving-notification-from-common-controls_1.cpp)]

W tym momencie lokalizacji kursora myszy znajduje się w `cursorPos` obiektu.

## <a name="see-also"></a>Zobacz także

[Tworzenie i używanie kontrolek](../mfc/making-and-using-controls.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
