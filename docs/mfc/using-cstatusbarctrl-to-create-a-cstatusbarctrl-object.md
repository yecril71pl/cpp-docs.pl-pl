---
title: Używanie formantu CStatusBarCtrl do tworzenia obiektu CStatusBarCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CStatusBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb378bba1505f8bbc3739c070d52abe9ef4f8afc
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953830"
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>Używanie formantu CStatusBarCtrl do tworzenia obiektu CStatusBarCtrl
Oto przykład typowy sposób użycia protokołu [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md):  
  
### <a name="to-use-a-status-bar-control-with-parts"></a>Aby używać formantu paska stanu z części  
  
1.  Utworzyć `CStatusBarCtrl` obiektu.  
  
2.  Wywołanie [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight) Jeśli chcesz ustawić minimalną wysokość formantu paska stanu rysowania obszaru.  
  
3.  Wywołanie [SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor) Aby ustawić kolor tła formantu paska stanu.  
  
4.  Wywołanie [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) można ustawić stanu kontroli i Współrzędna prawej krawędzi każdej części paska części.  
  
5.  Wywołanie [SetText](../mfc/reference/cstatusbarctrl-class.md#settext) można ustawić tekst w ramach danego formantu paska stanu. Komunikat unieważnia części kontrolki, które uległy zmianie, co powoduje wyświetlanie nowego tekstu, gdy formant uzyskuje następny komunikat WM_PAINT.  
  
 W niektórych przypadkach na pasku stanu musi tylko do wyświetlania wiersza tekstu. W takim przypadku wywoływania [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple). To umieszcza formantu paska stanu w trybie "prosty", który wyświetla pojedynczą linie tekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

