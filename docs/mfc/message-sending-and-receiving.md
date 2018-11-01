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
ms.openlocfilehash: 95a54f3a518be19c7ae6f001e3096b825e64c0c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447401"
---
# <a name="message-sending-and-receiving"></a>Wysyłanie i odbieranie komunikatów

Należy wziąć pod uwagę wysyłanie części procesu i sposób reagowania platformę.

Większość wiadomości w wyniku interakcji z użytkownikiem w programie. Polecenia są generowane przez kliknięć myszą w menu i przycisków paska narzędzi lub naciśnięcia klawiszy skrótów. Użytkownik generuje również wiadomości Windows, na przykład przeniesienie lub zmiana rozmiaru okna. Inne komunikaty Windows są wysyłane po wystąpieniu zdarzenia, takie jak uruchamianie programu lub rozwiązanie, ponieważ windows Pobierz lub utraty fokus i tak dalej. Powiadamianie kontrolki komunikaty są generowane przez kliknięć myszą lub inne interakcje użytkownika za pomocą kontrolki, takie jak formant przycisku lub pola listy, w oknie dialogowym.

`Run` Funkcji składowej klasy typu `CWinApp` odczytuje komunikaty, a następnie wysyła je do odpowiedniego okna. Większość poleceń są wysyłane do ramki głównego okna aplikacji. `WindowProc` Wstępnie zdefiniowane przez pobiera biblioteki klas wiadomości i kieruje je w różny sposób, w zależności od kategorii odebranego komunikatu.

Teraz należy wziąć pod uwagę odbieranie część procesu.

Początkowa odbiorcy wiadomości musi być obiektem okna. Komunikaty Windows zwykle są obsługiwane bezpośrednio przez obiekt tego okna. Komunikaty poleceń, zwykle pochodzących z aplikacji głównej ramki okna Pobierz kierowane do łańcucha elemencie docelowym polecenia opisanego w [Routing poleceń](../mfc/command-routing.md).

Każdy obiekt, które są zdolne do otrzymywania wiadomości lub poleceń ma własną wiadomość mapowania tej pary wiadomości lub polecenie o nazwie jego obsługi.

Gdy obiekt docelowy polecenia odbiera wiadomości lub polecenia, wyszukuje jego mapy wiadomości pod kątem dopasowania. W przypadku odnalezienia programu obsługi wiadomości, wywołuje program obsługi. Aby uzyskać więcej informacji na temat sposobu mapy komunikatów są przeszukiwane zobacz [jak Framework wyszukiwania mapy wiadomości](../mfc/how-the-framework-searches-message-maps.md). Można ponownie znaleźć rysunku [polecenia w strukturze](../mfc/user-interface-objects-and-command-ids.md).

## <a name="see-also"></a>Zobacz też

[Jak struktura wywołuje programy obsługi](../mfc/how-the-framework-calls-a-handler.md)

