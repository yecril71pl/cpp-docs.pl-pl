---
title: "Używanie List obrazów z formantem paska pomocniczego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- image lists [MFC], rebar controls
- rebar controls [MFC], image lists
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 48eed1a72649d1f43bd86e6049d39dfe075c8b6f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="using-an-image-list-with-a-rebar-control"></a>Używanie listy obrazów z formantem paska pomocniczego
Każdej grupy paska pomocniczego może zawierać między innymi obraz z listy skojarzony obraz. Poniższa procedura zawiera szczegóły dotyczące czynności niezbędnych do wyświetlania obrazu w paśmie paska pomocniczego.  
  
### <a name="to-display-images-in-a-rebar-band"></a>Do wyświetlania obrazów w paśmie paska pomocniczego  
  
1.  Dołącz listy obrazów do obiektu formantu paska pomocniczego poprzez wywołanie [SetImageList](../mfc/reference/crebarctrl-class.md#setimagelist), przekazanie wskaźnika do istniejącej listy obrazów.  
  
2.  Modyfikowanie **REBARBANDINFO** struktury można przypisać do grupy paska pomocniczego obrazu:  
  
    -   Ustaw **fMask** członka **RBBIM_IMAGE**, przy użyciu bitowego operatora OR uwzględnienie dodatkowych flag odpowiednio do potrzeb.  
  
    -   Ustaw `iImage` elementu członkowskiego do indeksu listy obrazów obrazu do wyświetlenia.  
  
3.  Inicjuj wszystkie pozostałe elementy członkowskie danych, takich jak rozmiar, tekst i uchwyt okna podrzędnego zawartych w niej niezbędne informacje.  
  
4.  Wstaw nową grupę (przy użyciu obrazu) przy użyciu wywołania do [CReBarCtrl::InsertBand](../mfc/reference/crebarctrl-class.md#insertband), przechodzącą **REBARBANDINFO** struktury.  
  
 W poniższym przykładzie założono, że istniejący obiekt listy obrazów z dwa obrazy został dołączony do obiektu formantu paska pomocniczego (`m_wndReBar`). Nową grupę paska pomocniczego (zdefiniowane przez `rbi`), zawierający pierwszy obraz, jest dodawany przez wywołanie do `InsertBand`:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#28](../mfc/codesnippet/cpp/using-an-image-list-with-a-rebar-control_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Formanty](../mfc/controls-mfc.md)

