---
title: "Używanie list obrazów w formancie rozszerzonego pola kombi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- image lists [MFC], combo boxes
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: dfff25fe-af70-47a2-8032-3901d1e6842d
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3ac69e7d0dbe1748a409b107579c747b7f9a4a7c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-image-lists-in-an-extended-combo-box-control"></a>Używanie list obrazów w formancie rozszerzonego pola kombi
Funkcja main formantach rozszerzonego pola kombi jest możliwość kojarzenia obrazów z listy obrazów z poszczególnych elementów w formancie pola kombi. Każdy element nie może zostać wyświetlony trzy różne obrazy: jeden dla stan zaznaczenia, jedną dla nonselected stanu i innych obrazu nakładki.  
  
 Poniższa procedura umożliwia skojarzenie listy obrazów z formancie rozszerzonego pola kombi:  
  
### <a name="to-associate-an-image-list-with-an-extended-combo-box-control"></a>Aby skojarzyć listy obrazów z formancie rozszerzonego pola kombi  
  
1.  Utworzenia nowej listy obrazów (lub użyć istniejącego obiektu listy obraz), za pomocą [CImageList](../mfc/reference/cimagelist-class.md) Konstruktor i przechowywanie wynikowego wskaźnika.  
  
2.  Zainicjuj nowy obiekt listy obrazów, wywołując [CImageList::Create](../mfc/reference/cimagelist-class.md#create). Następujący kod jest przykładem tego wywołania.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#10](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_1.cpp)]  
  
3.  Dodaj opcjonalne obrazy dla każdego stanu możliwe: wybrany lub nonselected oraz nakładki. Poniższy kod dodaje trzy wstępnie zdefiniowanych obrazów.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#11](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_2.cpp)]  
  
4.  Skojarz listy obrazów z formantem w wyniku wywołania [CComboBoxEx::SetImageList](../mfc/reference/ccomboboxex-class.md#setimagelist).  
  
 Po listy obrazów został skojarzony z formantem, można określić pojedynczo, obrazy, każdy element będzie używany w przypadku trzy stany. Aby uzyskać więcej informacji, zobacz [Ustawianie obrazów dla pojedynczego elementu](../mfc/setting-the-images-for-an-individual-item.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Kontrolki](../mfc/controls-mfc.md)

