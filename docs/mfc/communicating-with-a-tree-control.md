---
title: Komunikacja z formantem drzewa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af0b248d5e32b535c23cc17b48efdd551dad7a2c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="communicating-with-a-tree-control"></a>Komunikacja z kontrolką drzewa
Użyj różnych metod wywoływania funkcji Członkowskich [CTreeCtrl](../mfc/reference/ctreectrl-class.md) obiektu, w zależności od sposobu utworzenia obiektu:  
  
-   Jeśli w oknie dialogowym do drzewa, użyj zmiennej elementu członkowskiego typu `CTreeCtrl` utworzony w klasie — okno dialogowe.  
  
-   Jeśli okno podrzędne formantu drzewa, użyj `CTreeCtrl` obiektu (lub wskaźnika) zostanie użyty do utworzenia obiektu.  
  
-   Jeśli używasz `CTreeView` obiektów, użyj funkcji [CTreeView::GetTreeCtrl](../mfc/reference/ctreeview-class.md#gettreectrl) Aby pobrać odwołanie do formantu drzewa. Możesz zainicjować innym odwołaniem o tej wartości lub przypisanie adresu odwołania do `CTreeCtrl` wskaźnika.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

