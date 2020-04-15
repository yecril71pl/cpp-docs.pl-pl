---
title: Mapy komunikatów (MFC)
ms.date: 09/07/2019
helpviewer_keywords:
- message maps [MFC], MFC
- Windows messages [MFC], message maps
- messages [MFC], Windows
- MFC, messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
ms.openlocfilehash: 8080becf1a1a153322bfd03cbd7006eaf2ce4e13
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356572"
---
# <a name="message-maps-mfc"></a>Mapy komunikatów (MFC)

W tej sekcji odwołania wymieniono wszystkie [makra mapowania wiadomości](../../mfc/reference/message-map-macros-mfc.md) i wszystkie wpisy [CWnd](../../mfc/reference/cwnd-class.md) message-map wraz z odpowiednimi prototypami funkcji członkowskich:

|Kategoria|Opis|
|--------------|-----------------|
|On\_command message handler (Program obsługi komunikatów polecenia ON COMMAND)|Obsługuje `WM_COMMAND` wiadomości generowane przez wybrane menu użytkownika lub klawisze dostępu do menu.|
|[Programy obsługi komunikatów powiadomień dotyczących okna podrzędnego](../../mfc/reference/child-window-notification-message-handlers.md)|Obsługa wiadomości powiadomień z okien podrzędnych.|
|[Programy obsługi wiadomości WM_](../../mfc/reference/handlers-for-wm-messages.md)|Obsługa `WM_` wiadomości, `WM_PAINT`takich jak .|
|[Programy obsługi wiadomości zdefiniowane przez użytkownika](../../mfc/reference/user-defined-handlers.md)|Obsługa komunikatów zdefiniowanych przez użytkownika.|

(Aby uzyskać wyjaśnienie terminologii i konwencji użytych w tym odwołaniu, zobacz [Jak korzystać z odsyłacza mapy wiadomości](../../mfc/reference/how-to-use-the-message-map-cross-reference.md).)

Ponieważ system Windows jest systemem operacyjnym zorientowanym na wiadomości, duża część programowania dla środowiska systemu Windows wymaga obsługi wiadomości. Za każdym razem, gdy wystąpi zdarzenie, takie jak naciśnięcie klawisza lub kliknięcie myszą, do aplikacji jest wysyłana wiadomość, która musi następnie obsługiwać zdarzenie.

Biblioteka klas Microsoft Foundation oferuje model programowania zoptymalizowany pod kątem programowania opartego na wiadomościach. W tym modelu "mapy wiadomości" są używane do określania, które funkcje będą obsługiwać różne komunikaty dla określonej klasy. Mapy wiadomości zawierają jedno lub więcej makr określających, które komunikaty będą obsługiwane przez które funkcje. Na przykład mapa wiadomości zawierająca `ON_COMMAND` makro może wyglądać mniej więcej tak:

[!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]

Makro `ON_COMMAND` służy do obsługi komunikatów poleceń generowanych przez menu, przyciski i klawisze akceleratora. [Makra](../../mfc/reference/message-map-macros-mfc.md) są dostępne do mapowania następujących elementów:

## <a name="windows-messages"></a>Wiadomości systemu Windows

- Powiadomienia kontrolne

- Komunikaty zdefiniowane przez użytkownika

## <a name="command-messages"></a>Komunikaty poleceń

- Zarejestrowane komunikaty zdefiniowane przez użytkownika

- Komunikaty aktualizacji interfejsu użytkownika

## <a name="ranges-of-messages"></a>Zakresy wiadomości

- Polecenia

- Aktualizowanie komunikatów obsługi

- Powiadomienia kontrolne

Chociaż makra mapy wiadomości są ważne, zazwyczaj nie trzeba ich używać bezpośrednio. Dzieje się tak, ponieważ [Kreator klas](mfc-class-wizard.md) automatycznie tworzy wpisy mapy wiadomości w plikach źródłowych, gdy jest używany do kojarzenia funkcji obsługi wiadomości z wiadomościami. Za każdym razem, gdy chcesz edytować lub dodać wpis mapy wiadomości, możesz użyć Kreatora zajęć.

> [!NOTE]
> Kreator klas nie obsługuje zakresów mapy wiadomości. Musisz napisać te wpisy mapy wiadomości samodzielnie.

Jednak mapy komunikatów są ważną częścią biblioteki klas Programu Microsoft Foundation. Należy zrozumieć, co robią, a dokumentacja jest dla nich.

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
