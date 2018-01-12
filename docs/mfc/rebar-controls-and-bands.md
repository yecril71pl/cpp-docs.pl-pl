---
title: Formanty paska pomocniczego i paski | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- rebar controls [MFC], working with bands in
- bands, in rebar controls
ms.assetid: b647e7a5-9ea7-48b1-8e5f-096d104748f0
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6426a25746858ed5bd7c0d8ef70575e029453bae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="rebar-controls-and-bands"></a>Formanty paska pomocniczego i paski
Głównym celem formantu paska pomocniczego ma działać jako kontener dla okien podrzędnych, formanty standardowe okno dialogowe, menu, paski narzędzi i tak dalej. Zawieranie ten jest obsługiwany przez pojęcie "poza pasmem". Każdej grupy paska pomocniczego może zawierać dowolną kombinację pasek uchwytu, mapy bitowej etykietę tekstową i okna podrzędnego.  
  
 Klasa `CReBarCtrl` wiele funkcji Członkowskich służy do pobierania i modyfikowania informacji dla przedziału określonego paska pomocniczego:  
  
-   [GetBandCount](../mfc/reference/crebarctrl-class.md#getbandcount) pobiera numer bieżącej paskami w formancie paska pomocniczego.  
  
-   [GetBandInfo](../mfc/reference/crebarctrl-class.md#getbandinfo) inicjuje **REBARBANDINFO** struktury o informacje z określonej grupy. Brak odpowiadającego [SetBandInfo](../mfc/reference/crebarctrl-class.md#setbandinfo) funkcję elementu członkowskiego.  
  
-   [GetRect](../mfc/reference/crebarctrl-class.md#getrect) pobiera prostokąt ograniczający określonej grupy.  
  
-   [GetRowCount](../mfc/reference/crebarctrl-class.md#getrowcount) pobiera liczbę wierszy poza pasmem w formancie paska pomocniczego.  
  
-   [IDToIndex](../mfc/reference/crebarctrl-class.md#idtoindex) pobiera indeks określonej grupy.  
  
-   [GetBandBorders](../mfc/reference/crebarctrl-class.md#getbandborders) pobiera obramowania grupy.  
  
 Oprócz manipulowanie kilka funkcji elementów członkowskich są pod warunkiem, które pozwalają na działanie w paskami pomocniczymi określonych.  
  
 [InsertBand](../mfc/reference/crebarctrl-class.md#insertband) i [DeleteBand](../mfc/reference/crebarctrl-class.md#deleteband) Dodawanie i usuwanie paskami pomocniczymi. [MinimizeBand](../mfc/reference/crebarctrl-class.md#minimizeband) i [MaximizeBand](../mfc/reference/crebarctrl-class.md#maximizeband) wpływa na rozmiar bieżącego taśmy szczególne paska pomocniczego. [MoveBand](../mfc/reference/crebarctrl-class.md#moveband) zmiany indeksu taśmy szczególne paska pomocniczego. [ShowBand](../mfc/reference/crebarctrl-class.md#showband) pokazuje lub ukrywa pasma paska pomocniczego od użytkownika.  
  
 W poniższym przykładzie pokazano, dodając pasek narzędzi (`m_wndToolBar`) do istniejącego formantu paska pomocniczego (`m_wndReBar`). Grupy jest opisane przez inicjowanie `rbi` struktury i wywołując `InsertBand` funkcji członkowskiej:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#27](../mfc/codesnippet/cpp/rebar-controls-and-bands_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

