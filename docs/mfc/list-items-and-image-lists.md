---
title: "Elementy listy, listy obrazów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 525d8353c308796d70f974fa56cde3aa76c12142
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="list-items-and-image-lists"></a>Elementy listy, listy obrazów
"Element" formantu listy ([CListCtrl](../mfc/reference/clistctrl-class.md)) składa się z ikony, etykiety i prawdopodobnie inne informacje (w "podelementy").  
  
 Ikony dla elementów kontrolki listy znajdują się na listach obrazów. Listy obrazów jeden zawiera ikony pełnym rozmiarze używane w widoku ikon. Listy obrazów drugie, opcjonalnie, zawiera mniejsze wersje tego samego ikon do użycia w innych widokach formantu. Trzeci opcjonalna lista zawiera obrazy "stan", takie jak pola wyboru do wyświetlenia przed małe ikony w niektórych widokach. Czwarty opcjonalna lista zawiera obrazy, które są wyświetlane w nagłówku poszczególne elementy kontrolki listy.  
  
> [!NOTE]
>  Kontrolka widoku listy zostanie utworzony z `LVS_SHAREIMAGELISTS` stylu, użytkownik jest odpowiedzialny za niszczenie listy obrazów, gdy są one już używane. Określ ten styl w przypadku przypisania tego samego obrazu listy do wielu kontrolki widok listy; w przeciwnym razie więcej niż jeden formant może podjąć próbę zniszczyć tej samej listy obrazów.  
  
 Aby uzyskać więcej informacji na temat elementów listy, zobacz [listy obrazów widok listy](http://msdn.microsoft.com/library/windows/desktop/bb774736) i [elementów i podelementów](http://msdn.microsoft.com/library/windows/desktop/bb774736) w zestawie Windows SDK. Zobacz też klasy [CImageList](../mfc/reference/cimagelist-class.md) w *odwołania MFC* i [przy użyciu CImageList](../mfc/using-cimagelist.md) w tej rodzinie artykułów.  
  
 Aby utworzyć kontrolkę listy, należy podać listy obrazów do użycia podczas wstawiania nowych elementów do listy. W poniższym przykładzie pokazano tej procedury, których `m_pImagelist` wskaźnika typu `CImageList` i `m_listctrl` jest `CListCtrl` element członkowski danych.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/cpp/list-items-and-image-lists_1.cpp)]  
  
 Jednak jeśli nie chcesz wyświetlać ikony w widoku listy lub formant listy, nie potrzebujesz listy obrazów.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CListCtrl](../mfc/using-clistctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

