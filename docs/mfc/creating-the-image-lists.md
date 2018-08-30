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
ms.openlocfilehash: 53cf33a551dc95e7ed282b599673f627ff8a7b21
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220940"
---
# <a name="creating-the-image-lists"></a>Tworzenie list obrazów
Tworzenie list obrazów jest taki sam, niezależnie od użycia [CListView](../mfc/reference/clistview-class.md) lub [CListCtrl](../mfc/reference/clistctrl-class.md).  
  
> [!NOTE]
>  Możesz tylko potrzebne obrazu listy jeśli zawiera kontrolki listy `LVS_ICON` stylu.  
  
 Używanie klasy `CImageList` utworzyć jedną lub więcej list obrazów (w przypadku ikony w pełnym rozmiarze małe ikony i Stany). Zobacz [CImageList](../mfc/reference/cimagelist-class.md)i zobacz [listy obrazów widok listy](/windows/desktop/Controls/using-list-view-controls) w zestawie Windows SDK.  
  
 Wywołaj [CListCtrl::SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) dla każdej listy obrazów; przekazać wskaźnik do odpowiedniego `CImageList` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CListCtrl](../mfc/using-clistctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

