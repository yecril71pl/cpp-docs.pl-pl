---
title: Crebar — vs. Crebarctrl — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CReBar
- CReBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a6d0b8df40676cc64c97a6bdef013321c404899f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="crebar-vs-crebarctrl"></a>Crebar — vs. CReBarCtrl
MFC oferuje dwie klasy, aby utworzyć pręty zbrojeniowe: [crebar —](../mfc/reference/crebar-class.md) i [crebarctrl —](../mfc/reference/crebarctrl-class.md) (który opakowuje interfejs API sterowania wspólne systemu Windows). **Crebar —** zawiera wszystkie funkcje formantu wspólnego paska pomocniczego i obsługuje wiele wymagane typowe ustawienia kontroli i struktur dla Ciebie.  
  
 `CReBarCtrl` to klasa otoki formantu paska pomocniczego Win32, który może być łatwiejsze do wdrożenia, jeśli nie chcesz zintegrować paska pomocniczego architekturę MFC. Jeśli planujesz używać `CReBarCtrl` i integrowanie paska pomocniczego architekturę MFC, należy zwrócić uwagę dodatkowe do komunikowania się manipulacje formantu paska pomocniczego z MFC. Ta komunikacja nie jest trudne; jest jednak dodatkowej pracy, który jest niepotrzebne, korzystając z **crebar —**.  
  
 Visual C++ udostępnia dwa sposoby, aby móc korzystać z formantu wspólnego paska pomocniczego.  
  
-   Tworzenie przy użyciu paska pomocniczego **crebar —**, a następnie wywołać [CReBar::GetReBarCtrl](../mfc/reference/crebar-class.md#getrebarctrl) uzyskać dostęp do `CReBarCtrl` funkcji elementów członkowskich.  
  
    > [!NOTE]
    >  `CReBar::GetReBarCtrl` jest wbudowaną funkcją elementu członkowskiego, który rzutuje **to** wskaźnika obiektu paska pomocniczego. Oznacza to, że w czasie wykonywania, wywołanie funkcji ma nie czynności.  
  
-   Tworzenie przy użyciu paska pomocniczego [crebarctrl —](../mfc/reference/crebarctrl-class.md)tego konstruktora.  
  
 Każda z tych metod zapewni Ci dostęp do funkcji Członkowskich formantu paska pomocniczego. Podczas wywoływania `CReBar::GetReBarCtrl`, zwraca odwołanie do `CReBarCtrl` obiektów, dzięki czemu można użyć albo zestaw funkcji elementów członkowskich. Zobacz [crebar —](../mfc/reference/crebar-class.md) informacji na temat tworzenia i tworzenie za pomocą paska pomocniczego **crebar —**.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

