---
title: Mapy komunikatów (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- message maps [MFC], MFC
- Windows messages [MFC], message maps
- messages [MFC], Windows
- MFC, messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
ms.openlocfilehash: 14c08a008456160fe817f066e5b22b06b9f9fa14
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611817"
---
# <a name="message-maps-mfc"></a>Mapy komunikatów (MFC)

Ta sekcja odwołania zawiera listę wszystkich [makra mapowania wiadomości](../../mfc/reference/message-map-macros-mfc.md) i wszystkie [CWnd](../../mfc/reference/cwnd-class.md) wpisy mapy komunikatów oraz odpowiedni element członkowski funkcji prototypy:

|Kategoria|Opis|
|--------------|-----------------|
|ON\_polecenia obsługi wiadomości|Obsługuje `WM_COMMAND` komunikaty generowane przez wybory menu użytkownika lub kluczy dostępu do menu.|
|[Programy obsługi komunikatów powiadomień dotyczących okna podrzędnego](../../mfc/reference/child-window-notification-message-handlers.md)|Obsługa komunikatów powiadomień z okien podrzędnych.|
|[Programy obsługi komunikatów WM_](../../mfc/reference/handlers-for-wm-messages.md)|Obsługa `WM_` komunikaty, takie jak `WM_PAINT`.|
|[Programy obsługi komunikatów zdefiniowanych przez użytkownika](../../mfc/reference/user-defined-handlers.md)|Obsługi komunikatów zdefiniowanych przez użytkownika.|

(Objaśnienia dotyczące terminologii i Konwencji używanych w ramach tego odwołania, zobacz [jak używanie odsyłacza mapy komunikatów](../../mfc/reference/how-to-use-the-message-map-cross-reference.md).)

Ponieważ Windows to system operacyjny ukierunkowane, dużą część Programowanie w środowisku Windows obejmuje Obsługa komunikatów. Występuje w każdym kliknij zdarzenie, takie jak myszy lub naciśnięcia klawisza, komunikat jest wysyłany do aplikacji, która następnie musi obsługiwać zdarzenia.

Bibliotekę Microsoft Foundation Class oferuje model programowania, zoptymalizowane pod kątem programowania oparta na komunikatach. W tym modelu "map komunikatów" są używane do wyznaczenia, jakie funkcje będzie obsługiwać różne komunikaty dla określonej klasy. Mapy komunikatów zawierają co najmniej jeden makra, które określają, wiadomości, które będzie obsługiwany przez który działa. Na przykład komunikat o mapy nadrzędnym `ON_COMMAND` — makro może wyglądać mniej więcej tak:

[!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]

`ON_COMMAND` Makro jest używane do obsługi wiadomości polecenia generowane przez menu, przyciski i klawiszy skrótów. [Makra](../../mfc/reference/message-map-macros-mfc.md) są dostępne następujące mapowania:

## <a name="windows-messages"></a>Windows wiadomości

- Powiadomień dotyczących formantu karty

- Zdefiniowane przez użytkownika wiadomości

## <a name="command-messages"></a>Komunikaty poleceń

- Zarejestrowane komunikaty zdefiniowanych przez użytkownika

- Komunikaty aktualizacji interfejsu użytkownika

## <a name="ranges-of-messages"></a>Zakresy wiadomości

- Polecenia

- Aktualizacja obsługi wiadomości

- Powiadomień dotyczących formantu karty

Mimo że makra map wiadomości są ważne, zazwyczaj nie trzeba używać ich bezpośrednio. Jest to spowodowane w oknie dialogowym właściwości automatycznie tworzy wpisy mapy komunikatów w plikach źródłowych, gdy używasz do skojarzenia z funkcji obsługi wiadomości za pomocą wiadomości. Zawsze, gdy chcesz edytować lub dodać wpis mapy wiadomości, można użyć w oknie właściwości.

> [!NOTE]
>  W oknie właściwości nie obsługuje zakresów map komunikatów. Należy napisać te wpisy mapy komunikatów samodzielnie.

Jednak mapy komunikatów są ważną częścią biblioteki klas Microsoft Foundation. Należy zrozumieć, co robią, a dokumentacja jest dostępna dla nich.

## <a name="see-also"></a>Zobacz także

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
