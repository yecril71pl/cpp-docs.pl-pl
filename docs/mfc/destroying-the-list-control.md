---
title: Likwidowanie formantu listy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fdaafb8a6951050dac0022e0e6e8874b48d688e7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="destroying-the-list-control"></a>Likwidowanie kontrolki listy
Po osadzeniu Twojej [CListCtrl](../mfc/reference/clistctrl-class.md) obiekt jako element członkowski danych klasy widoku lub w oknie dialogowym zostanie zniszczony, gdy zostanie zniszczony jego właściciela. Jeśli używasz [clistview —](../mfc/reference/clistview-class.md), platformę zniszczy formantu po jego niszczy widoku.  
  
 Rozmieszczania dla niektórych danych listy mają być przechowywane w aplikacji, a nie kontrolka listy należy zorganizować jego cofania alokacji. Aby uzyskać więcej informacji, zobacz [elementy wywołania zwrotnego i maska wywołania zwrotnego](http://msdn.microsoft.com/library/windows/desktop/bb774736) w zestawie Windows SDK.  
  
 Ponadto jest odpowiedzialny za dealokowanie żadnych list obrazów utworzona i skojarzona z listy obiektu formantu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CListCtrl](../mfc/using-clistctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

