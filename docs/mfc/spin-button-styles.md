---
title: Style przycisku pokrętła | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- styles [MFC], CSpinButtonCtrl
- CSpinButtonCtrl class [MFC], styles
- styles [MFC], spin button control
- spin button control, styles
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 96b559fcda4825aec71ba4b5c1dd8c3cd319b83d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="spin-button-styles"></a>Style przycisku pokrętła
Wiele ustawień pokrętła ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)) są kontrolowane przez style. Można ustawić następujące style przy użyciu **właściwości** okna edytora okien dialogowych.  
  
-   **Orientacja** pionowych lub poziomych. Określa orientację przycisk strzałki. Skojarzone z `UDS_HORZ` stylu.  
  
-   **Wyrównanie** odłączyć, lewej lub prawej. Określa położenie przycisku pokrętła. Lewy i prawy pozycji przycisku pokrętła obok okna zaprzyjaźnionego. Szerokość okna zaprzyjaźnionego jest obniżane, aby pomieścić przycisk pokrętła. Skojarzone z `UDS_ALIGNLEFT` i `UDS_ALIGNRIGHT` style.  
  
-   **Automatyczne Zaprzyjaźnianie** automatycznie wybiera poprzedniego okna w porządku osi Z jako zaprzyjaźnione okno do przycisku pokrętła. W szablonie okna dialogowego to poprzedzającego przycisk pokrętła kolejności tabulacji dla formantu. Skojarzone z `UDS_AUTOBUDDY` stylu.  
  
-   **Ustaw Buddy Integer** powoduje, że pokrętła zwiększyć i zmniejszyć podpis okna buddy jako bieżące zmiany pozycji. Skojarzone z `UDS_SETBUDDYINT` stylu.  
  
-   **Bez tysięcy** nie wstawia tysięcy separatora wartości w podpisie okna zaprzyjaźnionego. Skojarzone z `UDS_NOTHOUSANDS` stylu.  
  
    > [!NOTE]
    >  Ustawienie tego stylu, jeśli chcesz użyć wymiana danych okna dialogowego (DDX), aby uzyskać wartość całkowita z formantu partnera. `DDX_Text` nie akceptuje osadzonych separatory tysięcy.  
  
-   **Zawijaj** sprawia, że położenie "wrap", ponieważ wartość nie jest zwiększone lub zmniejszone poza zakresem formantu. Skojarzone z `UDS_WRAP` stylu.  
  
-   **Klawisze strzałek** powoduje, że przycisk pokrętła, aby zwiększyć lub zmniejszyć pozycja po naciśnięciu klawisza Strzałka w górę i Strzałka w dół. Skojarzone z `UDS_ARROWKEYS` stylu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

