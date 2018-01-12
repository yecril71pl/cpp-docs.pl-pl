---
title: Dodawanie kart do formantu karty | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 46012a265c1ecefa7af63f829be22e6132e036cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="adding-tabs-to-a-tab-control"></a>Dodawanie kart do formantu karty
Po utworzeniu formantu karty ([CTabCtrl](../mfc/reference/ctabctrl-class.md)), dodać dowolną liczbę kart.  
  
### <a name="to-add-a-tab-item"></a>Aby dodać element karty  
  
1.  Przygotowanie [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) struktury.  
  
2.  Wywołanie [CTabCtrl::InsertItem](../mfc/reference/ctabctrl-class.md#insertitem), przekazanie struktury.  
  
3.  Powtórz kroki 1 i 2 dla dodatkowych kartę elementów.  
  
 Aby uzyskać więcej informacji, zobacz [Tworzenie formantu karty](http://msdn.microsoft.com/library/windows/desktop/bb760550) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTabCtrl](../mfc/using-ctabctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

