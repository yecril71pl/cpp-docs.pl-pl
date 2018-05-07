---
title: Używanie formantów drzewa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CTreeCtrl class [MFC], using
- tree controls [MFC], about tree controls
ms.assetid: 4e92941a-e477-4fb1-b1ce-4abeafbef1c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5bd7210f2f63d55fc4244a6b88456ede1265c8e9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-tree-controls"></a>Używanie kontrolek drzewa
Typowy sposób formantu drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) jest zgodny ze wzorcem poniżej:  
  
-   Formant nie zostanie utworzony. Jeśli formant jest określona w szablonie — okno dialogowe lub jeśli używasz `CTreeView`, tworzenie odbywa się automatycznie po utworzeniu okna dialogowego lub widoku. Jeśli chcesz utworzyć drzewie jako okna podrzędnego niektóre inne okna, użyj [Utwórz](../mfc/reference/ctreectrl-class.md#create) funkcję elementu członkowskiego.  
  
-   Jeśli chcesz, aby używać obrazów formantu drzewa, ustaw listy obrazów, wywołując [SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist). Możesz również zmienić wcięcie, wywołując [SetIndent](../mfc/reference/ctreectrl-class.md#setindent). Jest to dobry moment, w tym celu w [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) (dla formantów w oknach dialogowych) lub [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) (dla widoków).  
  
-   Umieszczanie danych w formancie przez wywołanie metody `CTreeCtrl`w [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) funkcja raz dla każdego elementu danych. `InsertItem` Zwraca dojście do elementu, który służy do odwołuje się do niego później, takie jak kiedy dodawanie elementów podrzędnych. Odpowiedni moment, aby zainicjować danych jest w `OnInitDialog` (dla formantów w oknach dialogowych) lub `OnInitialUpdate` (dla widoków).  
  
-   Gdy użytkownik rozpocznie się za pomocą formantu, wysyła komunikaty powiadomień dotyczących różnych. Można określić funkcji do obsługi poszczególnych wiadomości mają być obsługiwane przez dodanie **on_notify_reflect —** makra mapy komunikatów okna kontrolki lub dodając `ON_NOTIFY` makra mapy komunikatów okna nadrzędnego. Zobacz [komunikaty powiadomień dotyczących formantu drzewa](../mfc/tree-control-notification-messages.md) dalszej części tego tematu listę możliwych powiadomienia.  
  
-   Wywołanie różnych funkcji członkowskich zestawu, aby ustawić wartości dla formantu. Zmiany, które można wprowadzić obejmują ustawianie wcięć i zmiana tekstu, obrazów lub dane skojarzone z elementem.  
  
-   Użyj różnych funkcji Get, sprawdź zawartość formantu. Można również przejść przez zawartość drzewie funkcje, dzięki którym można pobrać dojścia do elementów nadrzędnych i podrzędnych, elementów równorzędnych określonego elementu. Można nawet sortować element podrzędny określonego węzła.  
  
-   Gdy wszystko będzie gotowe za pomocą formantu, upewnij się, że poprawnie zostanie zniszczony. Jeśli formant drzewa jest w oknie dialogowym lub jeśli jest to widok go i `CTreeCtrl` obiektu zostaną automatycznie usunięte. Jeśli nie, musisz upewnij się, że oba formantu i `CTreeCtrl` obiektu prawidłowo zostaną zniszczone.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

