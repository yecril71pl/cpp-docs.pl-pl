---
title: Obsługa i mapowanie komunikatów
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, messages
- message handling [MFC]
- message maps [MFC]
ms.assetid: 62fe2a1b-944c-449d-a0f0-63c11ee0a3cb
ms.openlocfilehash: 0321d98d8b92af0b80259bc49e84e69b987577a4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508242"
---
# <a name="message-handling-and-mapping"></a>Obsługa i mapowanie komunikatów

W tym artykule opisano sposób przetwarzania komunikatów i poleceń przez środowisko MFC oraz sposób łączenia ich z funkcjami obsługi.

W tradycyjnych programach dla systemu Windows komunikaty systemu Windows są obsługiwane w dużej instrukcji switch w procedurze okna. MFC zamiast tego używa [map komunikatów](../mfc/message-categories.md) do mapowania bezpośrednich komunikatów do różnych funkcji składowych klasy. Mapy komunikatów są wydajniejsze niż funkcje wirtualne w tym celu i umożliwiają obsługę komunikatów przez najbardziej odpowiedni C++ obiekt — aplikację, dokument, widok itd. Można mapować pojedynczy komunikat lub zakres komunikatów, identyfikatory poleceń lub identyfikatory formantów.

Komunikaty WM_COMMAND — zwykle generowane przez menu, przyciski paska narzędzi lub akceleratory — również używają mechanizmu mapy komunikatów. MFC definiuje standardowy [Routing](../mfc/command-routing.md) komunikatów poleceń między aplikacją, oknem ramki, widokiem i aktywnymi dokumentami w programie. W razie potrzeby można przesłonić ten Routing.

Mapy komunikatów również umożliwiają aktualizowanie obiektów interfejsu użytkownika (takich jak menu i przyciski paska narzędzi), Włączanie lub wyłączanie ich w bieżącym kontekście.

Aby uzyskać ogólne informacje o komunikatach i kolejkach komunikatów w systemie Windows, zobacz [komunikaty i kolejki komunikatów](/windows/win32/winmsg/messages-and-message-queues) w Windows SDK.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md)

- [Jak struktura wywołuje procedurę obsługi komunikatów](../mfc/how-the-framework-calls-a-handler.md)

- [Jak struktura wyszukuje mapy komunikatów](../mfc/how-the-framework-searches-message-maps.md)

- [Deklarowanie funkcji obsługi komunikatów](../mfc/declaring-message-handler-functions.md)

- [Mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)

- [Jak wyświetlić informacje o poleceniu na pasku stanu](../mfc/how-to-display-command-information-in-the-status-bar.md)

- [Dynamiczna aktualizacja obiektów interfejsu użytkownika](../mfc/how-to-update-user-interface-objects.md)

- [Instrukcje: tworzenie mapy komunikatów dla klasy szablonów](../mfc/how-to-create-a-message-map-for-a-template-class.md)

## <a name="see-also"></a>Zobacz także

[Pojęcia](../mfc/mfc-concepts.md)<br/>
[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)<br/>
[Klasa CWnd](../mfc/reference/cwnd-class.md)<br/>
[Klasa CCmdTarget](../mfc/reference/ccmdtarget-class.md)
