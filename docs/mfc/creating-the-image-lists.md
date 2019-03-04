---
title: Tworzenie list obrazów
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: 844bfe71f7b03f299f57b0fd4558b7e9eacf67c2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265785"
---
# <a name="creating-the-image-lists"></a>Tworzenie list obrazów

Tworzenie list obrazów jest taki sam, niezależnie od użycia [CListView](../mfc/reference/clistview-class.md) lub [CListCtrl](../mfc/reference/clistctrl-class.md).

> [!NOTE]
>  Możesz tylko potrzebne obrazu listy jeśli zawiera kontrolki listy `LVS_ICON` stylu.

Używanie klasy `CImageList` utworzyć jedną lub więcej list obrazów (w przypadku ikony w pełnym rozmiarze małe ikony i Stany). Zobacz [CImageList](../mfc/reference/cimagelist-class.md)i zobacz [listy obrazów widok listy](/windows/desktop/Controls/using-list-view-controls) w zestawie Windows SDK.

Wywołaj [CListCtrl::SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) dla każdej listy obrazów; przekazać wskaźnik do odpowiedniego `CImageList` obiektu.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
