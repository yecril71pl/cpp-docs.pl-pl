---
title: "Zarządzanie bieżącym widokiem | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- views [MFC], and OnActivateView method [MFC]
- views [MFC], deactivating
- views [MFC], activating
- frame windows [MFC], current view
- OnActivateView method [MFC]
- views [MFC], current
- deactivating views [MFC]
- current view in frame window [MFC]
ms.assetid: 0a1cc22d-d646-4536-9ad2-3cb6d7092e4a
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 339a3677783b789c6026dc0e46c09cfdb1d2e451
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="managing-the-current-view"></a>Zarządzanie bieżącym widokiem
W ramach Domyślna implementacja ramka okna okno ramowe przechowuje informacje o aktualnie aktywny widok. Jeśli okno ramowe zawiera więcej niż jeden widok, na przykład w oknie podziału, bieżący widok jest najnowszych widoku w użyciu. Widok aktywny jest niezależna od aktywnego okna w systemie Windows lub bieżący fokus wprowadzania.  
  
 Podczas aktywnego widoku zmiany, platformę powiadamia bieżący widok przez wywołanie jego [OnActivateView](../mfc/reference/cview-class.md#onactivateview) funkcję elementu członkowskiego. Można określić, czy widok jest aktywowany lub dezaktywowany, sprawdzając `OnActivateView`w `bActivate` parametru. Domyślnie `OnActivateView` Ustawia fokus na bieżący widok aktywacji. Można zastąpić `OnActivateView` do wykonania dowolnego specjalnego przetwarzania, gdy widok jest dezaktywowany lub ponownej aktywacji. Na przykład można podać specjalne wizualnych, aby odróżnić widoku aktywnego od innych, nieaktywne widoki.  
  
 Okno ramowe przekazuje polecenia do bieżącego widoku (aktywny), zgodnie z opisem w [Routing poleceń](../mfc/command-routing.md), w ramach standardowego routingu poleceń.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie okien ramowych](../mfc/using-frame-windows.md)

