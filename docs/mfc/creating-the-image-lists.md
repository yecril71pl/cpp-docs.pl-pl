---
title: "Tworzenie list obrazów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4878caa735562a76bc4afe64b7d5bb1ecb22e069
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="creating-the-image-lists"></a>Tworzenie list obrazów
Tworzenie list obrazów jest taki sam, niezależnie od użycia [clistview —](../mfc/reference/clistview-class.md) lub [CListCtrl](../mfc/reference/clistctrl-class.md).  
  
> [!NOTE]
>  Możesz tylko muszą obrazu list Jeśli formantu listy zawiera `LVS_ICON` stylu.  
  
 Klasa `CImageList` można utworzyć jeden lub więcej list obrazów (w przypadku pełnym rozmiarze ikon Małe ikony i stanów). Zobacz [CImageList](../mfc/reference/cimagelist-class.md)i zobaczyć [listy obrazów widok listy](http://msdn.microsoft.com/library/windows/desktop/bb774736) w zestawie Windows SDK.  
  
 Wywołanie [CListCtrl::SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) dla każdego obraz listy; wskaźnikiem do odpowiedniego `CImageList` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CListCtrl](../mfc/using-clistctrl.md)   
 [Formanty](../mfc/controls-mfc.md)

