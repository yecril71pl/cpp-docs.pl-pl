---
title: "Dodawanie formantów do arkusza właściwości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- controls [MFC], adding to property sheets
- property sheets, adding controls
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2acbbed1a253a502aea8b19af6fd16ddb343e3ec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="adding-controls-to-a-property-sheet"></a>Dodawanie formantów do arkusza właściwości
Domyślnie arkusz właściwości przydziela obszar okien na stronach właściwości, indeks i przyciski OK, Anuluj i Zastosuj. (Niemodalnego arkusza właściwości nie ma OK, Anuluj i zastosować przycisków). Można dodać inne formanty do arkusza właściwości. Na przykład można dodać okno podglądu po prawej stronie obszaru strony właściwości do wyświetlenia użytkownika, jak bieżące ustawienia będzie wyglądać czy zastosowana do obiektu zewnętrznego.  
  
 Można dodawać formanty do okna dialogowego arkusz właściwości w `OnCreate` programu obsługi. Obsługa dodatkowych funkcji kontroli zwykle wymaga rozmiar okna dialogowego arkusza właściwości. Po wywołaniu metody klasy podstawowej **CPropertySheet::OnCreate**, wywołaj [GetWindowRect](../mfc/reference/cwnd-class.md#getwindowrect) uzyskać szerokość i wysokość okna arkusza właściwości aktualnie przydzielony, rozwiń węzeł prostokąta wymiarów i wywołanie [MoveWindow](../mfc/reference/cwnd-class.md#movewindow) Aby zmienić rozmiar okna arkusza właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Arkusze właściwości](../mfc/property-sheets-mfc.md)   
 [Cpropertypage — klasa](../mfc/reference/cpropertypage-class.md)   
 [Klasa CPropertySheet](../mfc/reference/cpropertysheet-class.md)
