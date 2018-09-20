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
ms.openlocfilehash: 7772b6b6a809e5a89e2cb6b0ef3edb68821805c2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372318"
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

