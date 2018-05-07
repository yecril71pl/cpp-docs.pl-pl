---
title: Dodawanie elementów do formantu nagłówka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69d64265a94df2770e3a234ab992130b4809f9e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="adding-items-to-the-header-control"></a>Dodawanie elementów do formantu nagłówka
Po utworzeniu formantu nagłówka ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) w jej okna nadrzędnego, Dodaj tyle "elementów nagłówka" zgodnie z potrzebami: zazwyczaj jest to jeden dla kolumny.  
  
### <a name="to-add-a-header-item"></a>Aby dodać element nagłówka  
  
1.  Przygotowanie [HD_ITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247) struktury.  
  
2.  Wywołanie [CHeaderCtrl::InsertItem](../mfc/reference/cheaderctrl-class.md#insertitem), przekazanie struktury.  
  
3.  Powtórz kroki 1 i 2 dla dodatkowych elementów.  
  
 Aby uzyskać więcej informacji, zobacz [Dodawanie elementów do formantu nagłówka](http://msdn.microsoft.com/library/windows/desktop/bb775238) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

