---
title: Komunikacja z formantem drzewa | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2ef1188c9519e57c8132a2b20fc3b272d6c0ac51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="communicating-with-a-tree-control"></a>Komunikacja z kontrolką drzewa
Użyj różnych metod wywoływania funkcji Członkowskich [CTreeCtrl](../mfc/reference/ctreectrl-class.md) obiektu, w zależności od sposobu utworzenia obiektu:  
  
-   Jeśli w oknie dialogowym do drzewa, użyj zmiennej elementu członkowskiego typu `CTreeCtrl` utworzony w klasie — okno dialogowe.  
  
-   Jeśli okno podrzędne formantu drzewa, użyj `CTreeCtrl` obiektu (lub wskaźnika) zostanie użyty do utworzenia obiektu.  
  
-   Jeśli używasz `CTreeView` obiektów, użyj funkcji [CTreeView::GetTreeCtrl](../mfc/reference/ctreeview-class.md#gettreectrl) Aby pobrać odwołanie do formantu drzewa. Możesz zainicjować innym odwołaniem o tej wartości lub przypisanie adresu odwołania do `CTreeCtrl` wskaźnika.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

