---
title: Elementy listy, listy obrazów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6e12c212939a708a4411a28bff0ebe5026a21b1e
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932133"
---
# <a name="list-items-and-image-lists"></a>Elementy listy, listy obrazów
"Element" formantu listy ([CListCtrl](../mfc/reference/clistctrl-class.md)) składa się z ikony, etykiety i prawdopodobnie inne informacje (w "podelementy").  
  
 Ikony dla elementów kontrolki listy znajdują się na listach obrazów. Listy obrazów jeden zawiera ikony pełnym rozmiarze używane w widoku ikon. Listy obrazów drugie, opcjonalnie, zawiera mniejsze wersje tego samego ikon do użycia w innych widokach formantu. Trzeci opcjonalna lista zawiera obrazy "stan", takie jak pola wyboru do wyświetlenia przed małe ikony w niektórych widokach. Czwarty opcjonalna lista zawiera obrazy, które są wyświetlane w nagłówku poszczególne elementy kontrolki listy.  
  
> [!NOTE]
>  Jeśli kontrolka widoku listy jest tworzony przy użyciu stylu LVS_SHAREIMAGELISTS, jest odpowiedzialny za niszczenie listy obrazów, gdy są one już używane. Określ ten styl w przypadku przypisania tego samego obrazu listy do wielu kontrolki widok listy; w przeciwnym razie więcej niż jeden formant może podjąć próbę zniszczyć tej samej listy obrazów.  
  
 Aby uzyskać więcej informacji na temat elementów listy, zobacz [listy obrazów widok listy](http://msdn.microsoft.com/library/windows/desktop/bb774736) i [elementów i podelementów](http://msdn.microsoft.com/library/windows/desktop/bb774736) w zestawie Windows SDK. Zobacz też klasy [CImageList](../mfc/reference/cimagelist-class.md) w *odwołania MFC* i [przy użyciu CImageList](../mfc/using-cimagelist.md) w tej rodzinie artykułów.  
  
 Aby utworzyć kontrolkę listy, należy podać listy obrazów do użycia podczas wstawiania nowych elementów do listy. W poniższym przykładzie pokazano tej procedury, których *m_pImagelist* wskaźnika typu `CImageList` i *m_listctrl* jest `CListCtrl` element członkowski danych.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/cpp/list-items-and-image-lists_1.cpp)]  
  
 Jednak jeśli nie chcesz wyświetlać ikony w widoku listy lub formant listy, nie potrzebujesz listy obrazów.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CListCtrl](../mfc/using-clistctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

