---
title: Tworzenie list obrazów
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: 6687b62b70103894d957a21019008e8781385feb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508784"
---
# <a name="creating-the-image-lists"></a>Tworzenie list obrazów

Tworzenie list obrazów jest takie samo, jak w przypadku używania [CListView](../mfc/reference/clistview-class.md) lub [CListCtrl](../mfc/reference/clistctrl-class.md).

> [!NOTE]
>  Tylko listy obrazów są potrzebne, Jeśli kontrolka listy zawiera `LVS_ICON` styl.

Użyj klasy `CImageList` , aby utworzyć co najmniej jedną listę obrazów (dla ikon o pełnym rozmiarze, małych ikon i Stanów). Zobacz [Korzystanie CImageList](../mfc/reference/cimagelist-class.md)i zobacz [listę obrazów widoku listy](/windows/win32/Controls/using-list-view-controls) w Windows SDK.

Wywołaj [CListCtrl:: SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) dla każdej listy obrazów; Przekaż wskaźnik do odpowiedniego `CImageList` obiektu.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
