---
title: Obsługa i mapowanie komunikatów
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, messages
- message handling [MFC]
- message maps [MFC]
ms.assetid: 62fe2a1b-944c-449d-a0f0-63c11ee0a3cb
ms.openlocfilehash: 41f3432b3741019a787ee24b0f508fe8e65e0470
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279669"
---
# <a name="message-handling-and-mapping"></a>Obsługa i mapowanie komunikatów

Rodzina tego artykułu opisano, jak komunikaty i polecenia są przetwarzane przez platformę, MFC i jak łącz je z ich funkcje obsługi.

W przypadku tradycyjnych programów dla Windows Windows komunikaty są obsługiwane w instrukcji switch dużych procedury okna. Zamiast tego używa MFC [komunikatu mapy](../mfc/message-categories.md) do mapowania bezpośredniej wiadomości funkcje składowych klasy distinct. Mapy komunikatów są bardziej wydajne niż funkcje wirtualne w tym celu i umożliwiają one wiadomości, które mają być obsługiwane przez najbardziej odpowiedniego obiektu języka C++ — aplikacji, dokumentu, widok i tak dalej. Można mapować pojedynczej wiadomości lub zakres komunikatów, identyfikatory poleceń lub kontroli identyfikatorów.

Wm_command — komunikaty — zwykle generowane przez menu, przyciski paska narzędzi lub akceleratorów — także użyć mechanizmu mapy komunikatów. MFC zdefiniowano standard [routingu](../mfc/command-routing.md) polecenia komunikatów między aplikacji, ramki okien, widok i dokumenty aktywne w programach. Możesz przesłonić to routingu, jeśli potrzebujesz.

Mapy komunikatów również podać sposób aktualizowania obiektów interfejsu użytkownika (takich jak menu i przycisków paska narzędzi), włączając lub wyłączając je do potrzeb bieżącego kontekstu.

Aby uzyskać ogólne informacje dotyczące wiadomości i kolejki komunikatów w Windows, zobacz [wiadomości i kolejki komunikatów](/windows/desktop/winmsg/messages-and-message-queues) w zestawie Windows SDK.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md)

- [Jak struktura wywołuje program obsługi komunikatów](../mfc/how-the-framework-calls-a-handler.md)

- [Jak struktura wyszukuje mapy komunikatów](../mfc/how-the-framework-searches-message-maps.md)

- [Deklarowanie funkcji obsługi komunikatów](../mfc/declaring-message-handler-functions.md)

- [Mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)

- [Sposób wyświetlania informacji o poleceniu na pasku stanu](../mfc/how-to-display-command-information-in-the-status-bar.md)

- [Aktualizacja dynamiczna obiektów interfejsu użytkownika](../mfc/how-to-update-user-interface-objects.md)

- [Instrukcje: Tworzenie mapy komunikatów dla klasy szablonów](../mfc/how-to-create-a-message-map-for-a-template-class.md)

## <a name="see-also"></a>Zobacz także

[Pojęcia](../mfc/mfc-concepts.md)<br/>
[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)<br/>
[Klasa CWnd](../mfc/reference/cwnd-class.md)<br/>
[Klasa CCmdTarget](../mfc/reference/ccmdtarget-class.md)
