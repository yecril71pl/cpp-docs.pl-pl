---
title: "Tworzenie list obrazów | Dokumentacja firmy Microsoft"
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
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bfb42dc2c14b5092aeb667ea22008abe4d581a6f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="creating-the-image-lists"></a>Tworzenie list obrazów
Tworzenie list obrazów jest taki sam, niezależnie od użycia [clistview —](../mfc/reference/clistview-class.md) lub [CListCtrl](../mfc/reference/clistctrl-class.md).  
  
> [!NOTE]
>  Możesz tylko muszą obrazu list Jeśli formantu listy zawiera `LVS_ICON` stylu.  
  
 Klasa `CImageList` można utworzyć jeden lub więcej list obrazów (w przypadku pełnym rozmiarze ikon Małe ikony i stanów). Zobacz [CImageList](../mfc/reference/cimagelist-class.md)i zobaczyć [listy obrazów widok listy](http://msdn.microsoft.com/library/windows/desktop/bb774736) w zestawie Windows SDK.  
  
 Wywołanie [CListCtrl::SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) dla każdego obraz listy; wskaźnikiem do odpowiedniego `CImageList` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CListCtrl](../mfc/using-clistctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

