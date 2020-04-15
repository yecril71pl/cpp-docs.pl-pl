---
title: Gdzie można znaleźć mapy komunikatów
ms.date: 11/04/2016
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
ms.openlocfilehash: eec0ae43546e3cc0c08e3178c4808e21fa48686a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360165"
---
# <a name="where-to-find-message-maps"></a>Gdzie można znaleźć mapy komunikatów

Podczas tworzenia nowej aplikacji szkielet za pomocą Kreatora aplikacji, Kreator aplikacji zapisuje mapę wiadomości dla każdej klasy docelowej polecenia, którą tworzy dla Ciebie. Obejmuje to klasy aplikacji pochodnej, dokumentu, widoku i okna ramki. Niektóre z tych map wiadomości mają już wpisy dostarczone przez Kreatora aplikacji dla niektórych wiadomości i wstępnie zdefiniowanych poleceń, a niektóre są tylko symbolami zastępczymi dla programów obsługi, które zostaną dodane.

Mapa wiadomości klasy znajduje się w pliku . CPP dla klasy. Pracując z podstawowymi mapami komunikatów, które tworzy Kreator aplikacji, za pomocą [Kreatora klas](reference/mfc-class-wizard.md) można dodawać wpisy dla wiadomości i poleceń, które każda klasa będzie obsługiwać. Po dodaniu niektórych wpisów typowa mapa komunikatów może wyglądać następująco:

[!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]

Mapa wiadomości składa się z kolekcji makr. Dwa makra, [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) i [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map), nawias mapy wiadomości. Inne makra, `ON_COMMAND`takie jak , wypełnić zawartość mapy wiadomości.

> [!NOTE]
> Po makrach mapy wiadomości nie następują średniki.

Kreator dodawania klasy służy do tworzenia nowej klasy, udostępnia on mapę komunikatów dla klasy. Alternatywnie można utworzyć mapę wiadomości ręcznie za pomocą edytora kodu źródłowego.

## <a name="see-also"></a>Zobacz też

[Jak struktura wyszukuje mapy komunikatów](../mfc/how-the-framework-searches-message-maps.md)
