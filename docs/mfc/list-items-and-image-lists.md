---
title: Elementy listy, listy obrazów
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
ms.openlocfilehash: cae387dc028df46a7891e68d49f5f0c5a89126c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571044"
---
# <a name="list-items-and-image-lists"></a>Elementy listy, listy obrazów

"Element" w kontrolce listy ([CListCtrl](../mfc/reference/clistctrl-class.md)) składa się z ikony, etykietę i ewentualnie inne informacje (w "podelementy").

Ikony dla elementów kontrolki listy znajdują się na listach obrazów. Jeden listy obrazów zawiera pełny ikony używane w widoku ikon. Listy obrazów w drugim, opcjonalnie, zawiera mniejsze wersje tego samego ikon do użytku w innych widokach formantu. Trzeci opcjonalna lista zawiera obrazy "stan", takie jak pola wyboru, do wyświetlenia przed małych ikon w niektórych widokach. Czwarty opcjonalna lista zawiera obrazy, które są wyświetlane w nagłówku poszczególnych elementów formantu listy.

> [!NOTE]
>  Jeśli kontrolka widoku listy jest tworzona przy użyciu stylu LVS_SHAREIMAGELISTS, ponosisz odpowiedzialność za zniszczenie list obrazów, gdy są one już używane. Określ ten styl, w przypadku przypisania tego samego obrazu, który zawiera listę do wielu formantów widoku listy; w przeciwnym razie więcej niż jeden formant może próbować zniszczyć tej samej listy obrazów.

Aby uzyskać więcej informacji na temat elementów listy, zobacz [listy obrazów widok listy](/windows/desktop/Controls/using-list-view-controls) i [elementów i podelementów](/windows/desktop/Controls/using-list-view-controls) w zestawie Windows SDK. Zobacz też klasy [CImageList](../mfc/reference/cimagelist-class.md) w *odwołanie MFC* i [korzystanie z CImageList](../mfc/using-cimagelist.md) w tej rodzinie artykułów.

Aby utworzyć kontrolkę listy, należy podać listy obrazów do użycia podczas wstawiania nowych elementów do listy. W poniższym przykładzie pokazano tej procedury, gdzie *m_pImagelist* jest wskaźnikiem typu `CImageList` i *m_listctrl* jest `CListCtrl` element członkowski danych.

[!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/cpp/list-items-and-image-lists_1.cpp)]

Jednak jeśli nie zamierzasz wyświetlać ikony w widoku listy lub kontrolka listy, nie potrzebujesz list obrazów.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

