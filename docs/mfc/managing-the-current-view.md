---
title: Zarządzanie bieżącym widokiem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 09d29f4bc0b62e5824209759d45e63c1d9e2daa6
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928743"
---
# <a name="managing-the-current-view"></a>Zarządzanie bieżącym widokiem
W ramach Domyślna implementacja ramka okna okno ramowe przechowuje informacje o aktualnie aktywny widok. Jeśli okno ramowe zawiera więcej niż jeden widok, na przykład w oknie podziału, bieżący widok jest najnowszych widoku w użyciu. Widok aktywny jest niezależna od aktywnego okna w systemie Windows lub bieżący fokus wprowadzania.  
  
 Podczas aktywnego widoku zmiany, platformę powiadamia bieżący widok przez wywołanie jego [OnActivateView](../mfc/reference/cview-class.md#onactivateview) funkcję elementu członkowskiego. Można określić, czy widok jest aktywowany lub dezaktywowany, sprawdzając `OnActivateView`w *bActivate* parametru. Domyślnie `OnActivateView` Ustawia fokus na bieżący widok aktywacji. Można zastąpić `OnActivateView` do wykonania dowolnego specjalnego przetwarzania, gdy widok jest dezaktywowany lub ponownej aktywacji. Na przykład można podać specjalne wizualnych, aby odróżnić widoku aktywnego od innych, nieaktywne widoki.  
  
 Okno ramowe przekazuje polecenia do bieżącego widoku (aktywny), zgodnie z opisem w [Routing poleceń](../mfc/command-routing.md), w ramach standardowego routingu poleceń.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie okien ramowych](../mfc/using-frame-windows.md)

