---
title: Pochodne mapy komunikatów
ms.date: 11/19/2018
helpviewer_keywords:
- message handling [MFC], derived message handlers
- messages, routing
- message maps [MFC], derived
- derived message maps
ms.assetid: 21829556-6e64-40c3-8279-fed85d99de77
ms.openlocfilehash: fcdff67c57e932e414a2b61b28cd0498ab997c60
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173591"
---
# <a name="derived-message-maps"></a>Pochodne mapy komunikatów

Podczas komunikatów, obsługa, sprawdzanie komunikatów tej klasy mapy jest koniec wątku mapie komunikatów. Co się stanie, jeśli klasa `CMyView` (pochodną `CView`) ma żadnego pasującego wpisu wiadomości

Należy pamiętać, że `CView`, klasa bazowa `CMyView`, z kolei pochodzi od `CWnd`. Ten sposób `CMyView` *jest* `CView` i *jest* `CWnd`. Każda z tych klas ma swój własny mapy komunikatów. Rysunek "Widok hierarchii" poniżej przedstawia hierarchiczną relację klasy, ale należy pamiętać, że `CMyView` obiekt jest pojedynczy obiekt, który ma właściwości wszystkich trzech klasach.

![Hierarchia widoku](../mfc/media/vc38621.gif "hierarchii to widok") <br/>
Wyświetl hierarchię

Jeśli komunikat nie można dopasować w klasie `CMyView`w mapie komunikatów, struktura wyszukuje również mapę komunikatów w klasie bazowej natychmiastowe. `BEGIN_MESSAGE_MAP` — Makro na początku mapy komunikatów określa nazwy dwóch klas jako jego argumenty:

[!code-cpp[NVC_MFCMessageHandling#2](../mfc/codesnippet/cpp/derived-message-maps_1.cpp)]

Pierwszy argument nazwy klasy, do której należy mapie komunikatów. Drugi argument zapewnia połączenie z bezpośrednim klasy bazowej — `CView` tutaj — dlatego ramach wyszukiwać za jego mapie komunikatów.

Programy obsługi komunikatów, które podano w klasie bazowej związku z tym są dziedziczone przez klasy pochodnej. To bardzo podobna do normalnego wirtualny element członkowski funkcji bez konieczności Tworzenie wirtualnego wszystkie funkcje składowe programu obsługi.

Jeśli żadna procedura obsługi nie zostanie znaleziony w żadnym z mapy komunikatów klasy bazowej, przetwarzanie domyślnego komunikatu jest wykonywane. Jeśli komunikat jest poleceniem, struktura kieruje je do następnej elemencie docelowym polecenia. Jeśli jest standardową wiadomość Windows, komunikat jest przekazywany do odpowiedniej domyślną procedurę okna.

Aby przyśpieszyć dopasowania mapy komunikatów, struktura buforuje ostatnie dopasowanie prawdopodobieństwo, że będzie ona otrzymywać tego samego komunikatu ponownie. W wyniku tego jest procesy framework bardzo wydajne nieobsługiwany wiadomości. Mapy komunikatów są również miejsce skuteczniejsze od implementacji, które używają funkcji wirtualnych.

## <a name="see-also"></a>Zobacz także

[Jak struktura wyszukuje mapy komunikatów](../mfc/how-the-framework-searches-message-maps.md)
