---
title: "Używanie formantu CToolTipCtrl do tworzenia obiektu CToolTipCtrl i operowania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CToolTipCtrl
dev_langs:
- C++
helpviewer_keywords:
- tool tips [MFC], creating
- CToolTipCtrl class [MFC], using
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: da4c98e327d2d78050410e75869c894d73324281
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-ctooltipctrl-to-create-and-manipulate-a-ctooltipctrl-object"></a>Używanie formantu CToolTipCtrl do tworzenia obiektu CToolTipCtrl i operowania nim
Oto przykład [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) użycia:  
  
### <a name="to-create-and-manipulate-a-ctooltipctrl"></a>Do tworzenia i modyfikowania CToolTipCtrl  
  
1.  Utworzyć `CToolTipCtrl` obiektu.  
  
2.  Wywołanie [Utwórz](../mfc/reference/ctooltipctrl-class.md#create) Utwórz wspólne formantem etykietki narzędzia systemu Windows i dołączenie go do `CToolTipCtrl` obiektu.  
  
3.  Wywołanie [AddTool](../mfc/reference/ctooltipctrl-class.md#addtool) Aby zarejestrować narzędzia z formantem etykietki narzędzia informacji przechowywanych w etykietka narzędzia, która jest wyświetlana, gdy kursor znajduje się w narzędziu.  
  
4.  Wywołanie [SetToolInfo](../mfc/reference/ctooltipctrl-class.md#settoolinfo) można ustawić informacje, które obsługuje etykietki narzędzia dla narzędzia.  
  
5.  Wywołanie [SetToolRect](../mfc/reference/ctooltipctrl-class.md#settoolrect) można ustawić nowy prostokąt ograniczający narzędzia.  
  
6.  Wywołanie [HitTest](../mfc/reference/ctooltipctrl-class.md#hittest) do testowania wskaż określają, czy znajduje się on w prostokątem danego narzędzia, a jeśli tak, można pobrać informacji o narzędziu.  
  
7.  Wywołanie [GetToolCount](../mfc/reference/ctooltipctrl-class.md#gettoolcount) można pobrać liczby narzędzi zarejestrowany z formantem etykietki narzędzia.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

