---
title: "Używanie formantów drzewa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CTreeCtrl class [MFC], using
- tree controls [MFC], about tree controls
ms.assetid: 4e92941a-e477-4fb1-b1ce-4abeafbef1c1
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2ffbcf504b6b4a7af210b970bcc0f7d4f7e4876c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="using-tree-controls"></a>Używanie kontrolek drzewa
Typowy sposób formantu drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) jest zgodny ze wzorcem poniżej:  
  
-   Formant nie zostanie utworzony. Jeśli formant jest określona w szablonie — okno dialogowe lub jeśli używasz `CTreeView`, tworzenie odbywa się automatycznie po utworzeniu okna dialogowego lub widoku. Jeśli chcesz utworzyć drzewie jako okna podrzędnego niektóre inne okna, użyj [Utwórz](../mfc/reference/ctreectrl-class.md#create) funkcję elementu członkowskiego.  
  
-   Jeśli chcesz, aby używać obrazów formantu drzewa, ustaw listy obrazów, wywołując [SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist). Możesz również zmienić wcięcie, wywołując [SetIndent](../mfc/reference/ctreectrl-class.md#setindent). Jest to dobry moment, w tym celu w [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) (dla formantów w oknach dialogowych) lub [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) (dla widoków).  
  
-   Umieszczanie danych w formancie przez wywołanie metody `CTreeCtrl`w [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) funkcja raz dla każdego elementu danych. `InsertItem`Zwraca dojście do elementu, który służy do odwołuje się do niego później, takie jak kiedy dodawanie elementów podrzędnych. Odpowiedni moment, aby zainicjować danych jest w `OnInitDialog` (dla formantów w oknach dialogowych) lub `OnInitialUpdate` (dla widoków).  
  
-   Gdy użytkownik rozpocznie się za pomocą formantu, wysyła komunikaty powiadomień dotyczących różnych. Można określić funkcji do obsługi poszczególnych wiadomości mają być obsługiwane przez dodanie **on_notify_reflect —** makra mapy komunikatów okna kontrolki lub dodając `ON_NOTIFY` makra mapy komunikatów okna nadrzędnego. Zobacz [komunikaty powiadomień dotyczących formantu drzewa](../mfc/tree-control-notification-messages.md) dalszej części tego tematu listę możliwych powiadomienia.  
  
-   Wywołanie różnych funkcji członkowskich zestawu, aby ustawić wartości dla formantu. Zmiany, które można wprowadzić obejmują ustawianie wcięć i zmiana tekstu, obrazów lub dane skojarzone z elementem.  
  
-   Użyj różnych funkcji Get, sprawdź zawartość formantu. Można również przejść przez zawartość drzewie funkcje, dzięki którym można pobrać dojścia do elementów nadrzędnych i podrzędnych, elementów równorzędnych określonego elementu. Można nawet sortować element podrzędny określonego węzła.  
  
-   Gdy wszystko będzie gotowe za pomocą formantu, upewnij się, że poprawnie zostanie zniszczony. Jeśli formant drzewa jest w oknie dialogowym lub jeśli jest to widok go i `CTreeCtrl` obiektu zostaną automatycznie usunięte. Jeśli nie, musisz upewnij się, że oba formantu i `CTreeCtrl` obiektu prawidłowo zostaną zniszczone.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Formanty](../mfc/controls-mfc.md)

