---
title: "Tworzenie formantu nagłówka | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CHeaderCtrl class [MFC], creating
- header controls [MFC], creating
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 33f536a86a21e56eb36e546109f916ae5d6ca806
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="creating-the-header-control"></a>Tworzenie formantu nagłówka
Formantu nagłówka nie jest bezpośrednio dostępny w edytorze okien dialogowych (mimo że można dodać kontrolkę listy, w tym formancie nagłówka).  
  
### <a name="to-put-a-header-control-in-a-dialog-box"></a>Aby umieścić kontrolkę nagłówka w oknie dialogowym  
  
1.  Ręcznie osadzić zmiennej elementu członkowskiego typu [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) w klasy okien dialogowych.  
  
2.  W [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), tworzenie i ustawianie stylów dla `CHeaderCtrl`, umieść go i wyświetl ją.  
  
3.  Dodawanie elementów do formantu nagłówka.  
  
4.  Użyj okna właściwości do mapowania funkcje programu obsługi w klasy okien dialogowych dla wszystkich powiadomień formantu nagłówka wiadomości musi obsłużyć (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)).  
  
### <a name="to-put-a-header-control-in-a-view-not-a-clistview"></a>Aby ustawić formantu nagłówka w widoku (nie clistview —)  
  
1.  Osadź [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) obiektów w klasie widoku.  
  
2.  Styl, pozycja i wyświetlenia okna formantu nagłówka w widoku [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) funkcję elementu członkowskiego.  
  
3.  Dodawanie elementów do formantu nagłówka.  
  
4.  Użyj okna właściwości do mapowania funkcje obsługi klasy widoku dla wszystkich powiadomień formantu nagłówka wiadomości musi obsłużyć (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)).  
  
 W obu przypadkach obiekt formantu osadzonego jest tworzony, gdy tworzony jest obiekt widoku lub okna dialogowego. Należy wywołać [CHeaderCtrl::Create](../mfc/reference/cheaderctrl-class.md#create) można utworzyć okna formantu. Aby umieścić formantu, należy wywołać [CHeaderCtrl::Layout](../mfc/reference/cheaderctrl-class.md#layout) do określenia początkowy rozmiar i położenie formantu i [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos) można ustawić wymagane miejsce. Następnie dodaj elementy zgodnie z opisem w [Dodawanie elementów do formantu nagłówka](../mfc/adding-items-to-the-header-control.md).  
  
 Aby uzyskać więcej informacji, zobacz [Tworzenie formantu nagłówka](http://msdn.microsoft.com/library/windows/desktop/bb775238) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

