---
title: Gdzie można znaleźć mapy komunikatów
ms.date: 11/04/2016
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
ms.openlocfilehash: d9b9a50062334822f34047b8e22e67541ccaa952
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62217864"
---
# <a name="where-to-find-message-maps"></a>Gdzie można znaleźć mapy komunikatów

Podczas tworzenia nowego szkielet aplikacji za pomocą Kreatora aplikacji, Kreator aplikacji zapisuje mapy komunikatów dla każdej klasy elemencie docelowym polecenia, który tworzy za Ciebie. W tym aplikacji pochodnej, dokumentów, widok i klasy okien ramowych. Niektóre z tych mapy komunikatów już wpisy dostarczonych przez Kreatora aplikacji dla określonych wiadomości i poleceń wstępnie zdefiniowanych i niektóre są tylko symbole zastępcze dla programów obsługi, które mają być dodane.

Klasa mapy komunikatów znajduje się w. Plik CPP dla klasy. Praca z mapami wiadomości podstawowe, tworzonych przez Kreatora aplikacji, użyj okna właściwości dodać wpisy dla wiadomości i poleceń, które będą obsługiwać każdej klasy. Po dodaniu niektóre wpisy mapy komunikatów typowe może wyglądać następująco:

[!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]

Mapy komunikatów składa się z kolekcji makr. Dwa makra [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) i [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map), dopasowywanie mapie komunikatów. Innych makr, takich jak `ON_COMMAND`, wypełnij zawartość w mapie komunikatów.

> [!NOTE]
>  Makra mapy komunikatów nie zostanie zastosowane przy użyciu średników.

Korzystając z Kreatora dodawania klasy do utworzenia nowej klasy, zapewnia mapy komunikatów dla klasy. Alternatywnie można utworzyć mapy komunikatów ręcznie przy użyciu Edytor kodu źródłowego.

## <a name="see-also"></a>Zobacz także

[Jak struktura wyszukuje mapy komunikatów](../mfc/how-the-framework-searches-message-maps.md)
