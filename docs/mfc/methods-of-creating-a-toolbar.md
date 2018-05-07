---
title: Metody tworzenia paska narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CToolBarCtrl class [MFC], and CToolBar class [MFC]
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- toolbar controls [MFC]
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: f19d8d65-d49f-445c-abe8-d47d3e4101c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 052f1578386746f9a4d9892576f09b3b61547289
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="methods-of-creating-a-toolbar"></a>Metody tworzenia paska narzędzi
MFC oferuje dwie klasy, aby utworzyć paski narzędzi: [ctoolbar —](../mfc/reference/ctoolbar-class.md) i [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) (który opakowuje interfejs API sterowania wspólne systemu Windows). `CToolBar` zawiera wszystkie funkcje formantu wspólnego narzędzi i obsługuje wiele wymagane typowe ustawienia kontroli i struktur dla Ciebie; jednak wynikowego pliku wykonywalnego zazwyczaj będzie większy niż utworzony przy użyciu `CToolBarCtrl`.  
  
 `CToolBarCtrl` zazwyczaj powoduje mniejsze pliku wykonywalnego, a może chcieć użyć `CToolBarCtrl` Jeśli nie zamierzasz integrowanie narzędzi architekturę MFC. Jeśli planujesz używać `CToolBarCtrl` i integrowanie narzędzi architekturę MFC, należy zwrócić uwagę dodatkowe do komunikowania się manipulacji formantu paska narzędzi MFC. Ta komunikacja nie jest trudne; jest jednak dodatkowej pracy, który jest niepotrzebne, korzystając z `CToolBar`.  
  
 Visual C++ udostępnia dwa sposoby, aby móc korzystać z formantu wspólnego narzędzi.  
  
-   Tworzenie przy użyciu narzędzi `CToolBar`, a następnie wywołać [CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl) uzyskać dostęp do `CToolBarCtrl` funkcji elementów członkowskich.  
  
-   Tworzenie przy użyciu narzędzi [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)tego konstruktora.  
  
 Każda z tych metod zapewni Ci dostęp do funkcji Członkowskich formantu toolbar. Podczas wywoływania `CToolBar::GetToolBarCtrl`, zwraca odwołanie do `CToolBarCtrl` obiektów, dzięki czemu można użyć albo zestaw funkcji elementów członkowskich. Zobacz [ctoolbar —](../mfc/reference/ctoolbar-class.md) informacji na temat tworzenia i utworzenie przy użyciu narzędzi `CToolBar`.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

