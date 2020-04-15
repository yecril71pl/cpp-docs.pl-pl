---
title: Elementy listy, listy obrazów
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
ms.openlocfilehash: d378c6e07280349f9995981ad794039ebc015b25
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353051"
---
# <a name="list-items-and-image-lists"></a>Elementy listy, listy obrazów

"Element" w formancie listy ([CListCtrl](../mfc/reference/clistctrl-class.md)) składa się z ikony, etykiety i ewentualnie innych informacji (w "podelementów").

Ikony elementów kontroli listy znajdują się na listach obrazów. Jedna lista obrazów zawiera pełnowymiarowe ikony używane w widoku ikony. Druga, opcjonalna lista obrazów zawiera mniejsze wersje tych samych ikon do użycia w innych widokach formantu. Trzecia lista opcjonalna zawiera obrazy "state", takie jak pola wyboru, do wyświetlania przed małymi ikonami w niektórych widokach. Czwarta lista opcjonalna zawiera obrazy, które są wyświetlane w poszczególnych elementach nagłówka formantu listy.

> [!NOTE]
> Jeśli formant widoku listy jest tworzony przy użyciu stylu LVS_SHAREIMAGELISTS, użytkownik jest odpowiedzialny za niszczenie list obrazów, gdy nie są już używane. Określ ten styl, jeśli te same listy obrazów są przypisywane do wielu kontrolek widoku listy; w przeciwnym razie więcej niż jeden formant może próbować zniszczyć tę samą listę obrazów.

Aby uzyskać więcej informacji na temat elementów listy, zobacz [Listy obrazów widoku listy](/windows/win32/Controls/using-list-view-controls) listy listy i elementy i [podjedny](/windows/win32/Controls/using-list-view-controls) w zestawie Windows SDK. Zobacz także klasy [CImageList](../mfc/reference/cimagelist-class.md) w *odwołaniu MFC* i [przy użyciu CImageList](../mfc/using-cimagelist.md) w tej rodzinie artykułów.

Aby utworzyć kontrolkę listy, należy podać listy obrazów, które mają być używane podczas wstawiania nowych elementów do listy. Poniższy przykład pokazuje tę procedurę, gdzie *m_pImagelist* jest `CImageList` wskaźnikiem typu i `CListCtrl` *m_listctrl* jest elementem członkowskim danych.

[!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/cpp/list-items-and-image-lists_1.cpp)]

Jeśli jednak nie planujesz wyświetlania ikon w widoku listy lub formancie listy, nie potrzebujesz list obrazów.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Formanty](../mfc/controls-mfc.md)
