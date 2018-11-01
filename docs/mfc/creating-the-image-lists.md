---
title: Tworzenie list obrazów
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: 52f375c98b5f73e0f5721c951c94e4b24f0bc224
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608683"
---
# <a name="creating-the-image-lists"></a>Tworzenie list obrazów

Tworzenie list obrazów jest taki sam, niezależnie od użycia [CListView](../mfc/reference/clistview-class.md) lub [CListCtrl](../mfc/reference/clistctrl-class.md).

> [!NOTE]
>  Możesz tylko potrzebne obrazu listy jeśli zawiera kontrolki listy `LVS_ICON` stylu.

Używanie klasy `CImageList` utworzyć jedną lub więcej list obrazów (w przypadku ikony w pełnym rozmiarze małe ikony i Stany). Zobacz [CImageList](../mfc/reference/cimagelist-class.md)i zobacz [listy obrazów widok listy](/windows/desktop/Controls/using-list-view-controls) w zestawie Windows SDK.

Wywołaj [CListCtrl::SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) dla każdej listy obrazów; przekazać wskaźnik do odpowiedniego `CImageList` obiektu.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

