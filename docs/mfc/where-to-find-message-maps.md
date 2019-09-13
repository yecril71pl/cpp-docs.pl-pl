---
title: Gdzie można znaleźć mapy komunikatów
ms.date: 11/04/2016
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
ms.openlocfilehash: c50c6fc1134f579859530972dc864103c4e0ebcf
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907372"
---
# <a name="where-to-find-message-maps"></a>Gdzie można znaleźć mapy komunikatów

Podczas tworzenia nowej aplikacji szkieletowej za pomocą Kreatora aplikacji Kreator aplikacji zapisuje mapę komunikatów dla każdej klasy docelowej polecenia, którą tworzy dla Ciebie. Obejmuje to pochodne klasy aplikacji, dokumentów, widoków i okien ramowych. Niektóre z tych map komunikatów mają już wpisy dostarczone przez Kreatora aplikacji dla niektórych komunikatów i wstępnie zdefiniowanych poleceń, a niektóre z nich są tylko symbolami zastępczymi dla programów obsługi, które dodasz.

Mapa komunikatów klasy znajduje się w. Plik CPP dla klasy. Pracując z podstawowymi mapami komunikatów tworzonymi przez Kreatora aplikacji, należy użyć [kreatora klas](reference/mfc-class-wizard.md) do dodania wpisów dla komunikatów i poleceń, które będą obsługiwane przez każdą z klas. Typowy Mapa komunikatów może wyglądać następująco po dodaniu wpisów:

[!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]

Mapa wiadomości składa się z kolekcji makr. Dwa makra, [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) i [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map), przekładają się na mapę komunikatów. Inne makra, takie jak `ON_COMMAND`, wypełniają zawartość mapy komunikatów.

> [!NOTE]
>  Makra mapy komunikatów nie są poprzedzone średnikami.

W przypadku tworzenia nowej klasy przy użyciu Kreatora dodawania klas, udostępnia on mapę komunikatów dla klasy. Alternatywnie można utworzyć mapę wiadomości ręcznie przy użyciu edytora kodu źródłowego.

## <a name="see-also"></a>Zobacz także

[Jak struktura wyszukuje mapy komunikatów](../mfc/how-the-framework-searches-message-maps.md)
