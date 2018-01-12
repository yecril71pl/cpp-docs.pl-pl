---
title: "Zmienianie stylów formantu listy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6758cce9ab42c0dea490dd8ac9803588edceac5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="changing-list-control-styles"></a>Zmienianie stylów kontrolki listy
Można zmienić styl okna kontrolki listy ([CListCtrl](../mfc/reference/clistctrl-class.md)) w dowolnym momencie po jego utworzeniu. Zmieniając styl okna, możesz zmienić typ widoku, który korzysta z kontrolki. Na przykład, aby emulować Eksploratora, użytkownik może dostarczyć elementów menu lub przycisków paska narzędzi do przełączenia kontrola między różne widoki: widoku ikony, widok listy i tak dalej.  
  
 Na przykład po wybraniu elementu menu, możesz wykonać wywołania do [GetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633584) można pobrać bieżącego styl formantu, a następnie wywołać [SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591) zresetować styl. Aby uzyskać więcej informacji, zobacz [za pomocą kontrolki widok listy](http://msdn.microsoft.com/library/windows/desktop/bb774736) w zestawie Windows SDK.  
  
 Dostępne style są wymienione w [Utwórz](../mfc/reference/clistctrl-class.md#create). Style `LVS_ICON`, `LVS_SMALLICON`, `LVS_LIST`, i `LVS_REPORT` wyznaczyć widoki kontrolne cztery listy.  
  
## <a name="extended-styles"></a>Rozszerzone style  
 Oprócz standardowych stylów formantu listy istnieje inny zestaw określonych jako rozszerzone style. Te style omówione w [rozszerzone style widoku listy](http://msdn.microsoft.com/library/windows/desktop/bb774732) w zestawie Windows SDK udostępniać różne przydatne funkcje, które dostosowują zachowanie formantu listy. Aby zaimplementować zachowanie dany styl (np. wybór hover), wywoływania [CListCtrl::SetExtendedStyle](../mfc/reference/clistctrl-class.md#setextendedstyle), przekazywanie wymagane stylu. W poniższym przykładzie pokazano wywołanie funkcji:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]  
  
> [!NOTE]
>  Do wyboru aktywowany do pracy, musi mieć jedną **LVS_EX_ONECLICKACTIVATE** lub **LVS_EX_TWOCLICKACTIVATE** włączona.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CListCtrl](../mfc/using-clistctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

