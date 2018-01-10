---
title: "Operowanie formantem postępu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CProgressCtrl class [MFC], working with
- progress controls [MFC], manipulating
- CProgressCtrl class [MFC], manipulating
- controlling progress controls [MFC]
- CProgressCtrl class [MFC], using
ms.assetid: 9af561d1-980b-4003-a6da-ff79be15bf23
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c75866cdcf947745db741a6626f01215e58932e3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="manipulating-the-progress-control"></a>Operowanie formantem postępu
Istnieją trzy sposoby zmiany bieżącej pozycji formantu postępu ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)).  
  
-   Pozycja można zmieniać za ilość predefiniowany przyrostu.  
  
-   Pozycja może zostać zmienione przez dowolnej ilości.  
  
-   Pozycja można zmienić na określoną wartość.  
  
### <a name="to-change-the-position-by-a-preset-amount"></a>Aby zmienić pozycję przez ilość predefiniowany  
  
1.  Użyj [SetStep](../mfc/reference/cprogressctrl-class.md#setstep) funkcji członkowskiej, aby ustawić wartość przyrostu. Domyślnie ta wartość wynosi 10. Ta wartość jest zwykle ustawiana wśród początkowego ustawienia dla formantu. Wartość kroku może być ujemna.  
  
2.  Użyj [StepIt](../mfc/reference/cprogressctrl-class.md#stepit) funkcji członkowskiej, aby zwiększyć położenie. To powoduje, że formant do narysowania.  
  
    > [!NOTE]
    >  `StepIt`spowoduje, że położenie jest zawijane. Na przykład, dla danego zakresu 1 -100, krok 20 i pozycji 90, `StepIt` ustawi pozycji 10.  
  
### <a name="to-change-the-position-by-an-arbitrary-amount"></a>Aby zmienić pozycję przez dowolną kwotę  
  
1.  Użyj [OffsetPos](../mfc/reference/cprogressctrl-class.md#offsetpos) funkcji członkowskiej, aby zmienić pozycję. `OffsetPos`akceptuje wartości ujemnych.  
  
    > [!NOTE]
    >  `OffsetPos`, w odróżnieniu od `StepIt`, nie będzie zawijany położenie. Nowa pozycja jest dostosowywana do pozostają w zakresie.  
  
### <a name="to-change-the-position-to-a-specific-value"></a>Aby zmienić pozycję na określoną wartość  
  
1.  Użyj [SetPos](../mfc/reference/cprogressctrl-class.md#setpos) funkcji członkowskiej, aby umieścić na określoną wartość. Jeśli to konieczne, Nowa pozycja dostosowuje się w zakresie.  
  
 Zazwyczaj formantu postępu jest używany wyłącznie dla danych wyjściowych. Aby uzyskać bieżącą pozycję bez określenia nowej wartości, należy użyć [GetPos](../mfc/reference/cprogressctrl-class.md#getpos).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CProgressCtrl](../mfc/using-cprogressctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

