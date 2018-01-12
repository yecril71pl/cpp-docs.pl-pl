---
title: "Praca z formantem paska narzędzi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 475b44b856c874064a4ccbdaf7b648342eb9c657
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="working-with-the-toolbar-control"></a>Praca z formantem paska narzędzi
W tym artykule opisano, jak można pobrać [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) obiekt podstawowy [ctoolbar —](../mfc/reference/ctoolbar-class.md) uzyskać większą kontrolę nad pasków narzędzi. Jest to zaawansowane tematu.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>Aby dostęp do narzędzi formantu wspólnego źródłowego obiektu ctoolbar —  
  
1.  Wywołanie [CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl).  
  
 `GetToolBarCtrl`Zwraca odwołanie do [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) obiektu. Można użyć odwołania do wywołania funkcji elementów członkowskich klasy formantu paska narzędzi.  
  
> [!CAUTION]
>  Podczas wywoływania `CToolBarCtrl` **uzyskać** funkcji jest bezpieczne, jeśli wywołujesz należy zachować ostrożność **ustawić** funkcji. Jest to zaawansowane tematu. Zwykle nie należy dostęp do podstawowych formantu paska narzędzi.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Formanty (formanty standardowe systemu Windows)](../mfc/controls-mfc.md)  
  
-   [Podstawowe informacje na temat narzędzi](../mfc/toolbar-fundamentals.md)  
  
-   [Zadokowane i przestawne paski narzędzi](../mfc/docking-and-floating-toolbars.md)  
  
-   [Dynamiczne zmiany rozmiaru paska narzędzi](../mfc/docking-and-floating-toolbars.md)  
  
-   [Etykietki narzędzi paska narzędzi](../mfc/toolbar-tool-tips.md)  
  
-   [Aktualizacje paska stanu flyby —](../mfc/toolbar-tool-tips.md)  
  
-   [Obsługa powiadomień dotyczących etykietek narzędzi](../mfc/handling-tool-tip-notifications.md)  
  
-   [Ctoolbar —](../mfc/reference/ctoolbar-class.md) i [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) klas  
  
-   [Obsługa powiadomień dotyczących dostosowania](../mfc/handling-customization-notifications.md)  
  
-   [Wiele pasków narzędzi](../mfc/toolbar-fundamentals.md)  
  
-   [Używanie swoich starych pasków narzędzi](../mfc/using-your-old-toolbars.md)  
  
-   [Paski sterowania](../mfc/control-bars.md)  
  
 Aby uzyskać ogólne informacje o używaniu formanty standardowe systemu Windows, temacie [formanty standardowe](http://msdn.microsoft.com/library/windows/desktop/bb775493).  
  
## <a name="see-also"></a>Zobacz też  
 [MFC, implementacja paska narzędzi](../mfc/mfc-toolbar-implementation.md)

