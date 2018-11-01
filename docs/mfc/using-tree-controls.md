---
title: Używanie kontrolek drzewa
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], using
- tree controls [MFC], about tree controls
ms.assetid: 4e92941a-e477-4fb1-b1ce-4abeafbef1c1
ms.openlocfilehash: 2a42392253f158365af6bf9f7a5e4a1f4df93e95
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653407"
---
# <a name="using-tree-controls"></a>Używanie kontrolek drzewa

Typowy kontrolki drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) jest zgodna z wzorcem poniżej:

- Formant zostanie utworzony. Jeśli kontrolka została określona w szablonu okna dialogowego, lub jeśli używasz `CTreeView`, tworzenia jest automatycznie, gdy tworzony jest okno dialogowe lub widoku. Aby utworzyć formant drzewa jako okna podrzędnego niektóre inne okna, należy użyć [Utwórz](../mfc/reference/ctreectrl-class.md#create) funkcja elementu członkowskiego.

- Jeśli chcesz, aby używać obrazów kontrolki drzewa, ustaw listy obrazów, wywołując [SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist). Możesz również zmienić wcięcie, wywołując [SetIndent](../mfc/reference/ctreectrl-class.md#setindent). Jest dobry moment, w tym celu [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) (dla formantów w oknach dialogowych) lub [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) (dla widoków).

- Umieszczanie danych w formancie, wywołując `CTreeCtrl`firmy [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) funkcję jeden raz dla każdego elementu danych. `InsertItem` Zwraca uchwyt do elementu, który służy do odwoływania się do niego później, takie jak czas dodawania elementów podrzędnych. Jest odpowiedni moment, aby zainicjować dane `OnInitDialog` (dla formantów w oknach dialogowych) lub `OnInitialUpdate` (dla widoków).

- Jako użytkownik wchodzi w interakcję z kontrolką, wysyła komunikaty powiadomień dotyczących różnych. Można określić funkcję, która ma obsługiwać wszystkich wiadomości, które mają być obsługiwane przez dodanie on_notify_reflect — makro w mapie komunikatów okna kontrolki lub dodając ON_NOTIFY — makro do okna nadrzędnego mapy wiadomości. Zobacz [komunikaty powiadomień dotyczących kontrolki drzewa](../mfc/tree-control-notification-messages.md) później w tym temacie, aby uzyskać listę możliwych powiadomienia.

- Wywołaj różnych funkcji składowych zestawu, aby ustawić wartości dla formantu. Zmiany, które można wprowadzić obejmują, ustawianie wcięć i zmiana typu text, image lub dane skojarzone z elementem.

- Użyj różnych funkcji Get, aby sprawdzić zawartość formantu. Można również przechodzić zawartości formantu drzewa z funkcjami, które umożliwiają pobieranie dojścia do nadrzędne, podrzędne i elementów równorzędnych określonego elementu. Można nawet sortować elementy podrzędne określonego węzła.

- Gdy skończysz, za pomocą kontrolki, upewnij się, że jest prawidłowo niszczone. Jeśli formant drzewa jest w oknie dialogowym lub jeśli jest to widok go i `CTreeCtrl` obiekt jest niszczony automatycznie. Jeśli nie, musisz upewnij się, że obie kontrolki i `CTreeCtrl` obiektu są poprawnie niszczone.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

