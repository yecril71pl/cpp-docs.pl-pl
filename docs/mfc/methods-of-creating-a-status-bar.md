---
title: Metody tworzenia paska stanu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CStatusBar class [MFC], vs. CStatusBarCtrl
- methods [MFC], creating status bars
- CStatusBarCtrl class [MFC], vs. CStatusBar
- CStatusBarCtrl class [MFC], creating
- methods [MFC]
- status bars [MFC], creating
ms.assetid: 9aeaf290-7099-4762-a5ba-9c26705333c9
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f077c54902f69d181adbdfc8788f826f00239230
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="methods-of-creating-a-status-bar"></a>Metody tworzenia paska stanu
MFC oferuje dwie klasy, aby utworzyć paski stanu: [cstatusbar —](../mfc/reference/cstatusbar-class.md) i [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) (który opakowuje interfejs API sterowania wspólne systemu Windows). `CStatusBar`zawiera wszystkie funkcje stanu paska formantu wspólnego automatycznie interakcji z menu i pasków narzędzi i obsługuje wiele wymagane typowe ustawienia kontroli i struktur dla Ciebie; jednak wynikowego pliku wykonywalnego zazwyczaj będzie większy niż utworzony przy użyciu `CStatusBarCtrl`.  
  
 `CStatusBarCtrl`zazwyczaj powoduje mniejsze pliku wykonywalnego, a może chcieć użyć `CStatusBarCtrl` Jeśli nie zamierzasz integracji na pasku stanu z architektury MFC. Jeśli planujesz używać `CStatusBarCtrl` i integracji na pasku stanu z architektury MFC, należy zwrócić uwagę dodatkowe do komunikowania się pasek sterowania manipulacji MFC stanu. Ta komunikacja nie jest trudne; jest jednak dodatkowej pracy, który jest niepotrzebne, korzystając z `CStatusBar`.  
  
 Visual C++ udostępnia dwa sposoby, aby móc korzystać z formantu wspólnego paska stanu.  
  
-   Utwórz pasek przy użyciu stanu `CStatusBar`, a następnie wywołać [CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl) uzyskać dostęp do `CStatusBarCtrl` funkcji elementów członkowskich.  
  
-   Utwórz pasek przy użyciu stanu [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)tego konstruktora.  
  
 Każda z tych metod zapewni Ci dostęp do funkcji Członkowskich formantu paska stanu. Podczas wywoływania `CStatusBar::GetStatusBarCtrl`, zwraca odwołanie do `CStatusBarCtrl` obiektów, dzięki czemu można użyć albo zestaw funkcji elementów członkowskich. Zobacz [cstatusbar —](../mfc/reference/cstatusbar-class.md) informacji na temat tworzenia i tworzenia stanu paska przy użyciu `CStatusBar`.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Formanty](../mfc/controls-mfc.md)

