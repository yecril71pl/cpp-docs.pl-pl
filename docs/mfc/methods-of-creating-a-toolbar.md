---
title: "Metody tworzenia paska narzędzi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CToolBarCtrl class [MFC], and CToolBar class [MFC]
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- toolbar controls [MFC]
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: f19d8d65-d49f-445c-abe8-d47d3e4101c8
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2f9c6347768075ebd382dce87d1933796644bf61
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="methods-of-creating-a-toolbar"></a>Metody tworzenia paska narzędzi
MFC oferuje dwie klasy, aby utworzyć paski narzędzi: [ctoolbar —](../mfc/reference/ctoolbar-class.md) i [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) (który opakowuje interfejs API sterowania wspólne systemu Windows). `CToolBar`zawiera wszystkie funkcje formantu wspólnego narzędzi i obsługuje wiele wymagane typowe ustawienia kontroli i struktur dla Ciebie; jednak wynikowego pliku wykonywalnego zazwyczaj będzie większy niż utworzony przy użyciu `CToolBarCtrl`.  
  
 `CToolBarCtrl`zazwyczaj powoduje mniejsze pliku wykonywalnego, a może chcieć użyć `CToolBarCtrl` Jeśli nie zamierzasz integrowanie narzędzi architekturę MFC. Jeśli planujesz używać `CToolBarCtrl` i integrowanie narzędzi architekturę MFC, należy zwrócić uwagę dodatkowe do komunikowania się manipulacji formantu paska narzędzi MFC. Ta komunikacja nie jest trudne; jest jednak dodatkowej pracy, który jest niepotrzebne, korzystając z `CToolBar`.  
  
 Visual C++ udostępnia dwa sposoby, aby móc korzystać z formantu wspólnego narzędzi.  
  
-   Tworzenie przy użyciu narzędzi `CToolBar`, a następnie wywołać [CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl) uzyskać dostęp do `CToolBarCtrl` funkcji elementów członkowskich.  
  
-   Tworzenie przy użyciu narzędzi [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)tego konstruktora.  
  
 Każda z tych metod zapewni Ci dostęp do funkcji Członkowskich formantu toolbar. Podczas wywoływania `CToolBar::GetToolBarCtrl`, zwraca odwołanie do `CToolBarCtrl` obiektów, dzięki czemu można użyć albo zestaw funkcji elementów członkowskich. Zobacz [ctoolbar —](../mfc/reference/ctoolbar-class.md) informacji na temat tworzenia i utworzenie przy użyciu narzędzi `CToolBar`.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Formanty](../mfc/controls-mfc.md)

