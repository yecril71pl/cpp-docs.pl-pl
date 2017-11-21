---
title: "Używanie formantu CStatusBarCtrl do tworzenia obiektu CStatusBarCtrl | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CStatusBarCtrl
dev_langs: C++
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cf62df91b2952240e460c722c46c0221fb491227
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>Używanie formantu CStatusBarCtrl do tworzenia obiektu CStatusBarCtrl
Oto przykład typowy sposób użycia protokołu [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md):  
  
### <a name="to-use-a-status-bar-control-with-parts"></a>Aby używać formantu paska stanu z części  
  
1.  Utworzyć `CStatusBarCtrl` obiektu.  
  
2.  Wywołanie [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight) Jeśli chcesz ustawić minimalną wysokość formantu paska stanu rysowania obszaru.  
  
3.  Wywołanie [SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor) Aby ustawić kolor tła formantu paska stanu.  
  
4.  Wywołanie [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) można ustawić stanu kontroli i Współrzędna prawej krawędzi każdej części paska części.  
  
5.  Wywołanie [SetText](../mfc/reference/cstatusbarctrl-class.md#settext) można ustawić tekst w ramach danego formantu paska stanu. Komunikat unieważnia części kontrolki, które uległy zmianie, powodując go, aby wyświetlić nowy tekst, gdy formant obok uzyskuje `WM_PAINT` wiadomości.  
  
 W niektórych przypadkach na pasku stanu musi tylko do wyświetlania wiersza tekstu. W takim przypadku wywoływania [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple). To umieszcza formantu paska stanu w trybie "prosty", który wyświetla pojedynczą linie tekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Formanty](../mfc/controls-mfc.md)

