---
title: Mapy komunikatów (MFC)
ms.date: 09/07/2019
helpviewer_keywords:
- message maps [MFC], MFC
- Windows messages [MFC], message maps
- messages [MFC], Windows
- MFC, messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
ms.openlocfilehash: 4305d9b1db297eebcb189d2fad98b8c634ed1133
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908041"
---
# <a name="message-maps-mfc"></a>Mapy komunikatów (MFC)

W tej części odwołania znajduje się lista wszystkich [makr mapowania komunikatów](../../mfc/reference/message-map-macros-mfc.md) i wszystkie wpisy mapy komunikatów [CWnd](../../mfc/reference/cwnd-class.md) oraz odpowiadające im prototypy funkcji składowych:

|Kategoria|Opis|
|--------------|-----------------|
|Procedura obsługi komunikatów polecenia\_|Obsługuje `WM_COMMAND` komunikaty generowane przez opcje menu użytkownika lub klawisze dostępu menu.|
|[Programy obsługi komunikatów powiadomień dotyczących okna podrzędnego](../../mfc/reference/child-window-notification-message-handlers.md)|Obsługa komunikatów powiadomień z okien podrzędnych.|
|[Procedury obsługi komunikatów WM_](../../mfc/reference/handlers-for-wm-messages.md)|Obsługa `WM_` komunikatów, takich jak `WM_PAINT`.|
|[Procedury obsługi komunikatów zdefiniowane przez użytkownika](../../mfc/reference/user-defined-handlers.md)|Obsługa komunikatów zdefiniowanych przez użytkownika.|

(Aby uzyskać informacje na temat terminologii i Konwencji używanych w tym odwołaniu, zobacz [jak używać odsyłacza mapy komunikatów](../../mfc/reference/how-to-use-the-message-map-cross-reference.md).)

Ponieważ system Windows to system operacyjny zorientowany na komunikaty, znaczna część programowania środowiska systemu Windows obejmuje obsługę komunikatów. Za każdym razem, gdy występuje zdarzenie takie jak naciśnięcie klawisza lub kliknięcie myszą, do aplikacji jest wysyłany komunikat, który musi obsłużyć zdarzenie.

Biblioteka MFC oferuje model programowania zoptymalizowany pod kątem programowania opartego na wiadomościach. W tym modelu "mapy komunikatów" są używane do wyznaczania, które funkcje będą obsługiwać różne komunikaty dla określonej klasy. Mapy komunikatów zawierają co najmniej jedno makro określające, które komunikaty będą obsługiwane przez funkcje. Na przykład mapa komunikatów zawierająca `ON_COMMAND` makro może wyglądać następująco:

[!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]

`ON_COMMAND` Makro służy do obsługi komunikatów poleceń generowanych przez menu, przyciski i klawisze skrótów. Dostępne są [makra](../../mfc/reference/message-map-macros-mfc.md) umożliwiające zamapowanie następujących danych:

## <a name="windows-messages"></a>Komunikaty systemu Windows

- Powiadomienia sterujące

- Komunikaty zdefiniowane przez użytkownika

## <a name="command-messages"></a>Komunikaty poleceń

- Zarejestrowane komunikaty zdefiniowane przez użytkownika

- Komunikaty aktualizacji interfejsu użytkownika

## <a name="ranges-of-messages"></a>Zakresy komunikatów

- Polecenia

- Komunikaty procedury obsługi aktualizacji

- Powiadomienia sterujące

Mimo że makra mapy komunikatów są ważne, zazwyczaj nie trzeba ich używać bezpośrednio. Wynika to z faktu, że [Kreator klas](mfc-class-wizard.md) automatycznie tworzy wpisy mapy komunikatów w plikach źródłowych, gdy jest on używany do kojarzenia funkcji obsługi komunikatów z komunikatami. Za każdym razem, gdy chcesz edytować lub dodać wpis mapy komunikatów, możesz użyć kreatora klas.

> [!NOTE]
>  Kreator klas nie obsługuje zakresów map komunikatów. Musisz samodzielnie napisać te wpisy mapy komunikatów.

Jednak mapy komunikatów są ważną częścią biblioteka MFC. Należy zapoznać się z informacjami o tym, co robią.

## <a name="see-also"></a>Zobacz także

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
