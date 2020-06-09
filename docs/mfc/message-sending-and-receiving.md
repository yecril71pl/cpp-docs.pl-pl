---
title: Wysyłanie i odbieranie komunikatów
ms.date: 11/04/2016
helpviewer_keywords:
- Windows messages [MFC], handling in MFC
- control-notification messages [MFC]
- messages [MFC], receiving
- messages [MFC], MFC
- MFC, messages
- messages [MFC], sending
ms.assetid: 9ce189cb-b259-4c3b-b6f2-9cfbed18b98b
ms.openlocfilehash: 4da2fce68c1b6fd3827bc8b5d2a40dea5e5f117c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626175"
---
# <a name="message-sending-and-receiving"></a>Wysyłanie i odbieranie komunikatów

Rozważ wysłanie części procesu i sposobu reagowania struktury przez platformę.

Większość komunikatów wynika z interakcji użytkownika z programem. Polecenia są generowane przez kliknięcia myszą w elementach menu lub przyciski paska narzędzi lub naciśnięcie klawiszy skrótu. Użytkownik generuje również komunikaty systemu Windows, na przykład przenosząc lub zmieniając rozmiar okna. Inne komunikaty systemu Windows są wysyłane, gdy wystąpią zdarzenia, takie jak uruchamianie lub kończenie działania programu, gdy system Windows pobierze lub utraci fokus i tak dalej. Komunikaty sterujące — powiadomienia są generowane przez kliknięcia myszą lub inne interakcje użytkownika z kontrolką, takie jak kontrolka przycisk lub pole listy w oknie dialogowym.

`Run`Funkcja członkowska klasy `CWinApp` Pobiera komunikaty i wysyła je do odpowiedniego okna. Większość komunikatów poleceń jest wysyłanych do okna głównego ramki aplikacji. `WindowProc`Wstępnie zdefiniowane przez bibliotekę klas pobiera komunikaty i przekierowuje je inaczej, w zależności od kategorii odebranych komunikatów.

Teraz Rozważmy część otrzymującą proces.

Początkowy odbiornik wiadomości musi być obiektem okna. Komunikaty systemu Windows są zwykle obsługiwane bezpośrednio przez ten obiekt okna. Komunikaty poleceń, zazwyczaj pochodzące z głównego okna ramki aplikacji, są kierowane do łańcucha Target polecenia opisanego w temacie [routing poleceń](command-routing.md).

Każdy obiekt, który może odbierać wiadomości lub polecenia, ma swoją własną mapę komunikatów, która par wiadomości lub polecenie z nazwą jego obsługi.

Gdy obiekt docelowy polecenia odbiera komunikat lub polecenie przeszukuje mapę komunikatów pod kątem dopasowania. Jeśli odnajdzie procedurę obsługi dla wiadomości, wywoła procedurę obsługi. Aby uzyskać więcej informacji o sposobie wyszukiwania map komunikatów, zobacz [jak struktura przeszukuje mapy komunikatów](how-the-framework-searches-message-maps.md). Zapoznaj się ponownie z [poleceniami ilustracja w strukturze](user-interface-objects-and-command-ids.md).

## <a name="see-also"></a>Zobacz też

[Jak struktura wywołuje program obsługi](how-the-framework-calls-a-handler.md)
