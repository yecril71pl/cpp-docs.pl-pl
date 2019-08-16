---
title: Elementy listy, listy obrazów
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
ms.openlocfilehash: 77dd2f6a056ca74ff3334878a9cf1ef51c773335
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508359"
---
# <a name="list-items-and-image-lists"></a>Elementy listy, listy obrazów

Element "Item" w kontrolce listy ([CListCtrl](../mfc/reference/clistctrl-class.md)) składa się z ikony, etykiety i prawdopodobnie innych informacji (w "podelementach").

Ikony elementów formantów list są zawarte na listach obrazów. Jedna lista obrazów zawiera ikony o pełnym rozmiarze używane w widoku ikon. Druga, opcjonalna, lista obrazów zawiera mniejsze wersje tych samych ikon do użycia w innych widokach formantu. Trzecia lista opcjonalna zawiera obrazy stanu, takie jak pola wyboru, aby wyświetlić je przed małymi ikonami w niektórych widokach. Czwarta lista opcjonalna zawiera obrazy, które są wyświetlane w poszczególnych elementach nagłówka kontrolki listy.

> [!NOTE]
>  Jeśli kontrolka widok listy jest tworzona przy użyciu stylu LVS_SHAREIMAGELISTS, użytkownik jest odpowiedzialny za niszczenie list obrazów, gdy nie są one już używane. Określ ten styl, jeśli te same listy obrazów są przypisywane do wielu kontrolek widoku listy. w przeciwnym razie więcej niż jeden formant może próbować zniszczyć tę samą listę obrazów.

Aby uzyskać więcej informacji na temat elementów listy, zobacz [Wyświetlanie listy obrazów](/windows/win32/Controls/using-list-view-controls) i [elementów oraz](/windows/win32/Controls/using-list-view-controls) elementów podelementowych w Windows SDK. Zobacz też klasy [Korzystanie CImageList](../mfc/reference/cimagelist-class.md) w *dokumentacji MFC* i [Używanie korzystanie CImageList](../mfc/using-cimagelist.md) w tej rodzinie artykułów.

Aby utworzyć formant listy, należy podać listy obrazów, które będą używane podczas wstawiania nowych elementów do listy. Poniższy przykład ilustruje tę procedurę, gdzie *m_pImagelist* jest wskaźnikiem typu `CImageList` `CListCtrl` , a *m_listctrl* jest składową danych.

[!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/cpp/list-items-and-image-lists_1.cpp)]

Jeśli jednak nie planujesz wyświetlania ikon w widoku listy lub kontrolce listy, nie potrzebujesz list obrazów.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
