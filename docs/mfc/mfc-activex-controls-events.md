---
title: 'Kontrolki ActiveX MFC: Zdarzenia'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], events
- notifications [MFC], notifying containers of events
- custom events [MFC], adding to ActiveX controls
- events [MFC], mapping
- COleControl class [MFC], handling of events
- mappings [MFC], events
- stock events [MFC]
- container events [MFC]
- events [MFC], ActiveX controls
- OLE events [MFC]
ms.assetid: e1e57e0c-206b-4923-a0b5-682c26564f74
ms.openlocfilehash: 0d8a881d07a3e48673c6dc3298816d165273be0d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392677"
---
# <a name="mfc-activex-controls-events"></a>Kontrolki ActiveX MFC: Zdarzenia

Kontrolki ActiveX użyć zdarzenia, aby powiadomić kontener, który ma zdarzyło się coś do formantu. Typowe przykłady zdarzenia obejmują kliknięcia w kontrolce dane wprowadzane przy użyciu klawiatury i zmiany w stanie formantu. Gdy są wykonywane następujące akcje, formant uruchamia zdarzenie do wyzwalania alertu kontenera.

Zdarzenia są również nazywane wiadomości.

Biblioteka MFC obsługuje dwa rodzaje zdarzeń: standardowych i niestandardowych. Podstawowe zdarzenia są te zdarzenia, które klasy [COleControl](../mfc/reference/colecontrol-class.md) obsługuje automatycznie. Aby uzyskać pełną listę zdarzeń standardowych, zobacz artykuł [kontrolki ActiveX MFC: Dodawanie zdarzeń standardowych](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md). Zdarzenia niestandardowe umożliwiają kontrolki możliwość powiadamianie kontenera, które występuje, specyficzne dla tej kontrolki akcji. Niektóre przykłady będą zmiany wewnętrzny stan formantu lub odebranie komunikatu okna.

Kontrolki prawidłowo wyzwolenie zdarzenia klasy kontrolki musi być mapowane do funkcji składowej, która powinna być wywoływana, gdy wystąpi zdarzenie powiązane każdego zdarzenia formantu. Ten mechanizm mapowanie (nazywane mapę zdarzeń) umożliwia scentralizowanie informacje o zdarzeniu i zezwala programowi Visual Studio do łatwego dostępu i manipulowania zdarzenia obiektu Controls. Ta mapa zdarzeń jest deklarowana przez następujące makra, znajduje się w nagłówku (. H) pliku deklaracji klasy kontrolki:

[!code-cpp[NVC_MFC_AxUI#2](../mfc/codesnippet/cpp/mfc-activex-controls-events_1.h)]

Po Mapa zdarzeń została zadeklarowana, muszą być zdefiniowane w implementacji kontroli nad (. Plik CPP). Następujące wiersze kodu, zdefiniuj Mapa zdarzeń, umożliwiając kontroli nad ognia określonych zdarzeń:

[!code-cpp[NVC_MFC_AxUI#3](../mfc/codesnippet/cpp/mfc-activex-controls-events_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#4](../mfc/codesnippet/cpp/mfc-activex-controls-events_3.cpp)]

Jeśli używasz kreatora kontrolek ActiveX MFC do tworzenia projektu, automatycznie dodaje następujące wiersze. Jeśli nie używasz, Kreator kontrolek ActiveX MFC, należy ręcznie dodać następujące wiersze.

Za pomocą widoku klas można dodać podstawowe zdarzenia obsługiwane przez klasę `COleControl` lub zdarzeń niestandardowych, zdefiniowanych przez użytkownika. Dla każdego nowego zdarzenia w widoku klas automatycznie dodaje prawidłowego wpisu mapy zdarzeń formantów i kontrolki. Plik IDL.

Dwie inne artykuły omówiono zdarzenia szczegółowo:

- [Kontrolki ActiveX MFC: Dodawanie zdarzeń standardowych](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)

- [Kontrolki ActiveX MFC: dodawanie zdarzeń niestandardowych](../mfc/mfc-activex-controls-adding-custom-events.md)

## <a name="see-also"></a>Zobacz także

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: metody](../mfc/mfc-activex-controls-methods.md)<br/>
[Klasa COleControl](../mfc/reference/colecontrol-class.md)
