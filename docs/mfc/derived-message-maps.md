---
title: Pochodne mapy komunikatów
description: Opisuje obsługę komunikatów MFC.
ms.date: 09/23/2020
helpviewer_keywords:
- message handling [MFC], derived message handlers
- messages, routing
- message maps [MFC], derived
- derived message maps
ms.assetid: 21829556-6e64-40c3-8279-fed85d99de77
ms.openlocfilehash: 44c2180e441c91d34350c65bc17a53d1b650607c
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414220"
---
# <a name="derived-message-maps"></a>Pochodne mapy komunikatów

Podczas obsługi komunikatów sprawdzanie własnej mapy komunikatów klasy nie jest końcem wątku mapy komunikatów. Co się stanie, jeśli Klasa `CMyView` (pochodna z `CView` ) nie ma pasującego wpisu dla komunikatu?

Należy pamiętać, że `CView` Klasa bazowa `CMyView` , jest pochodną od `CWnd` . W ten sposób jest to `CMyView` *is* `CView` *is* i `CWnd` . Każda z tych klas ma własną mapę komunikatów. Na poniższym rysunku przedstawiono hierarchiczne relacje klas, ale należy pamiętać, że `CMyView` obiekt jest pojedynczym obiektem, który ma cechy wszystkich trzech klas.

![Hierarchia widoku](../mfc/media/vc38621.gif "Hierarchia widoku") <br/>
Hierarchia widoków

Jeśli nie można dopasować komunikatu do `CMyView` mapy komunikatów klasy, struktura przeszukuje także mapę wiadomości swojej bezpośredniej klasy podstawowej. `BEGIN_MESSAGE_MAP`Makro na początku mapy komunikatów określa dwie nazwy klas jako argumenty:

[!code-cpp[NVC_MFCMessageHandling#2](codesnippet/cpp/derived-message-maps_1.cpp)]

Pierwszy argument nazywa klasę, do której należy Mapa wiadomości. Drugi argument zapewnia połączenie z bezpośrednią klasą bazową, w tym przypadku `CView` , aby platforma mogła również przeszukiwać mapę komunikatów.

Procedury obsługi komunikatów podane w klasie bazowej są w ten sposób dziedziczone przez klasę pochodną. Jest to bardzo podobne do normalnych funkcji wirtualnych elementów członkowskich bez konieczności udostępniania wszystkich funkcji elementów członkowskich programu obsługi.

Jeśli żadna procedura obsługi nie zostanie znaleziona w żadnej z mapowań komunikatów klasy podstawowej, zostanie wykonane domyślne przetwarzanie komunikatu. Jeśli komunikat jest poleceniem, struktura kieruje go do następnego celu polecenia. Jeśli jest to standardowy komunikat systemu Windows, komunikat jest przesyłany do odpowiedniej procedury okna domyślnego.

Aby przyspieszyć dopasowanie mapy komunikatów, struktura buforuje ostatnie dopasowania na prawdopodobieństwo, że odbierze ten sam komunikat ponownie. Jedną z konsekwencji jest to, że struktura przetwarza nieobsłużone komunikaty w sposób dość wydajny. Mapy komunikatów są również bardziej wydajne niż implementacje korzystające z funkcji wirtualnych.

## <a name="see-also"></a>Zobacz także

[Jak struktura wyszukuje mapy komunikatów](how-the-framework-searches-message-maps.md)
