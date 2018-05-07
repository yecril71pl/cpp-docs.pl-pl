---
title: Używanie list obrazów w formancie rozszerzonego pola kombi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- image lists [MFC], combo boxes
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: dfff25fe-af70-47a2-8032-3901d1e6842d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c9a701871631fead48c22b1ffb2cbc3c386b960
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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

