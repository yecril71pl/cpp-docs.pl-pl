---
title: Tworzenie list obrazów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e5f5ac8396c32e56e4c0f2f951f45bb33714822
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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

