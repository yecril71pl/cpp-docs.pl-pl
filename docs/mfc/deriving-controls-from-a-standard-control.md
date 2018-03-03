---
title: "Wyprowadzanie formantów z formantu standardowego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- standard controls [MFC], deriving controls from
- common controls [MFC], deriving from
- derived controls
- controls [MFC], derived
- Windows common controls [MFC], deriving from
- standard controls
ms.assetid: a6f84315-7007-4e0e-8576-78be81254802
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2b93bc07fc5ab4680caaa276daaeca86189b8ce5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="deriving-controls-from-a-standard-control"></a>Wyprowadzanie formantów z formantu standardowego
Jako ze wszystkimi [CWnd](../mfc/reference/cwnd-class.md)-klasy, można zmodyfikować zachowanie formantu wyprowadzanie nowe klasy z istniejącej klasy formantu.  
  
### <a name="to-create-a-derived-control-class"></a>Można utworzyć klasy pochodnej formantu  
  
1.  Pochodzi z klasy z istniejącej klasy formantu i opcjonalnie Przesłoń **Utwórz** funkcji członkowskiej, dzięki czemu zapewnia argumenty niezbędne do klasy podstawowej **Utwórz** funkcji.  
  
2.  Podaj funkcji Członkowskich obsługi wiadomości i wpisy mapy wiadomości, aby zmodyfikować zachowanie formantu w odpowiedzi na określone komunikaty systemu Windows. Zobacz [mapowanie komunikatów na funkcje](../mfc/reference/mapping-messages-to-functions.md).  
  
3.  Podaj nowe funkcje Członkowskie mogą rozszerzyć funkcjonalność formantu (opcjonalnie).  
  
 Używanie pochodnej formantu w oknie dialogowym wymaga dodatkowej pracy. Typy i położenia kontrolki w oknie dialogowym zwykle są określone w zasobie szablonu okna dialogowego. W przypadku tworzenia klasy pochodnej formantu nie można określić go w szablonu okna dialogowego, ponieważ kompilator zasobów nie otrzymuje informacji o klasie pochodnej.  
  
#### <a name="to-place-your-derived-control-in-a-dialog-box"></a>Aby umieścić pochodnej formantu w oknie dialogowym  
  
1.  Osadź obiekt klasy pochodnej kontroli w deklaracji klasy pochodnej okien dialogowych.  
  
2.  Zastąpienie `OnInitDialog` funkcji członkowskiej WE klasy okien dialogowych do wywołania `SubclassDlgItem` funkcja członkowska, pochodnych formantu.  
  
 `SubclassDlgItem`"dynamicznie podklasy" formantu utworzone na podstawie szablonu okna dialogowego. W wypadku dynamicznie podklasy formantu zostanie przyłączanie się do systemu Windows, przetwarzania niektórych komunikatów w ramach własnej aplikacji, a następnie przekazuje pozostałych komunikatów systemu Windows. Aby uzyskać więcej informacji, zobacz [SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem) funkcji członkowskiej klasy `CWnd` w *odwołania MFC*. W poniższym przykładzie pokazano, jak mogą pisać zastępująca `OnInitDialog` do wywołania `SubclassDlgItem`:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#3](../mfc/codesnippet/cpp/deriving-controls-from-a-standard-control_1.cpp)]  
  
 Ponieważ pochodne formantu jest osadzony w klasy okien dialogowych, będzie wykonywane, gdy okno dialogowe jest tworzony i zostaną usunięte, gdy okno dialogowe zostanie zniszczony. Porównaj ten kod do przykładu w [dodawanie formantów strony By](../mfc/adding-controls-by-hand.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie i używanie formantów](../mfc/making-and-using-controls.md)   
 [Kontrolki](../mfc/controls-mfc.md)

