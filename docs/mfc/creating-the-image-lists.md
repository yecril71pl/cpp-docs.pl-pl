---
title: Tworzenie list obrazów
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: 440ab6fdfe7663557f6c6a6607e617c793d26674
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371573"
---
# <a name="creating-the-image-lists"></a>Tworzenie list obrazów

Tworzenie list obrazów jest takie samo, niezależnie od tego, czy używasz [CListView](../mfc/reference/clistview-class.md) lub [CListCtrl](../mfc/reference/clistctrl-class.md).

> [!NOTE]
> Listy obrazów są potrzebne tylko wtedy, gdy formant listy zawiera `LVS_ICON` styl.

Klasa `CImageList` służy do tworzenia jednej lub więcej list obrazów (w przypadku pełnowymiarowych ikon, małych ikon i stanów). Zobacz [CImageList](../mfc/reference/cimagelist-class.md)i zobacz [Listy obrazów widoku listy](/windows/win32/Controls/using-list-view-controls) w zestawie Windows SDK.

Wywołaj [CListCtrl::SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) dla każdej listy obrazów; przekazać wskaźnik do `CImageList` odpowiedniego obiektu.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Formanty](../mfc/controls-mfc.md)
