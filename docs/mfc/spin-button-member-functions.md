---
title: "Funkcje Członkowskie przycisku pokrętła | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- spin button control, methods
- CSpinButtonCtrl class [MFC], methods
ms.assetid: a08a26fd-b803-4cbe-a509-395fa357d057
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 57a2f9cfc5a95671eb21dabb91b8a83874341b76
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="spin-button-member-functions"></a>Funkcje członkowskie przycisku pokrętła
Istnieje kilka funkcji Członkowskich kontrolki pokrętła ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)). Użyj tych funkcji, aby zmienić następujące atrybuty przycisku pokrętła.  
  
-   **Akceleracja** można dostosować częstotliwość, przy którym pozycja zostanie zmieniona, gdy użytkownik posiada przycisk strzałki w dół. Aby pracować z przyspieszenia, użyj [SetAccel](../mfc/reference/cspinbuttonctrl-class.md#setaccel) i [GetAccel](../mfc/reference/cspinbuttonctrl-class.md#getaccel) funkcji elementów członkowskich.  
  
-   **Podstawowy** można zmienić base (10 lub 16) używany do wyświetlania położenie okna zaprzyjaźnionego w podpisie. Aby pracować z bazą, użyj [GetBase](../mfc/reference/cspinbuttonctrl-class.md#getbase) i [SetBase](../mfc/reference/cspinbuttonctrl-class.md#setbase) funkcji elementów członkowskich.  
  
-   **Kolega okna** dynamicznie można ustawić okna zaprzyjaźnionego. Aby zapytania lub zmień kontroli okna zaprzyjaźnionego, użyj [GetBuddy](../mfc/reference/cspinbuttonctrl-class.md#getbuddy) i [SetBuddy](../mfc/reference/cspinbuttonctrl-class.md#setbuddy) funkcji elementów członkowskich.  
  
-   **Pozycja** można zbadać i zmienić jego położenie. Aby pracować bezpośrednio z pozycji, użyj [GetPos](../mfc/reference/cspinbuttonctrl-class.md#getpos) i [SetPos](../mfc/reference/cspinbuttonctrl-class.md#setpos) funkcji elementów członkowskich. Ponieważ podpis formantu partnera mógł ulec zmianie (na przykład w przypadku czy partner jest formant edycyjny) `GetPos` pobiera bieżący podpis i w związku z tym można dostosować położenie.  
  
-   **Zakres** można zmienić położenia maksymalne i minimalne dla przycisku pokrętła. Domyślnie maksymalna jest ustawiona na 0, a minimalna jest równa 100. Ponieważ domyślna wartość maksymalna jest mniejsza niż minimalna domyślne, counter-intuitive jest akcje przycisk strzałki. Zazwyczaj zostanie ustawiony przy użyciu zakresu [SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) funkcję elementu członkowskiego. Zbadać użycie zakresu [GetRange](../mfc/reference/cspinbuttonctrl-class.md#getrange).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)   
 [Formanty](../mfc/controls-mfc.md)

