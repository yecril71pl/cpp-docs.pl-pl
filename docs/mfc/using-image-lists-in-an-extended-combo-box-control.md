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
ms.openlocfilehash: 080256f9a5de719e265009080036a3c0c2617118
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412239"
---
# <a name="using-image-lists-in-an-extended-combo-box-control"></a>Używanie list obrazów w formancie rozszerzonego pola kombi

Główna funkcja formantach rozszerzonego pola kombi jest zdolność do kojarzenia obrazów z listy obrazów z poszczególnych elementów w formancie pola kombi. Każdy element jest w stanie wyświetlić trzy różne obrazy: jeden dla wybranego stanu, po jednym dla jego nonselected stanu i innych obrazu nakładki.

Poniższa procedura kojarzy listy obrazów z formantu rozszerzonego pola kombi:

### <a name="to-associate-an-image-list-with-an-extended-combo-box-control"></a>Aby skojarzyć listy obrazów z formantu rozszerzonego pola kombi

1. Utworzenia nowej listy obrazów (lub użyj istniejącego obiektu listy obrazu), za pomocą [CImageList](../mfc/reference/cimagelist-class.md) Konstruktor i przechowywanie wynikowego wskaźnika.

1. Inicjowanie nowy obiekt listy obrazów, wywołując [CImageList::Create](../mfc/reference/cimagelist-class.md#create). Poniższy kod jest przykładem tego wywołania.

     [!code-cpp[NVC_MFCControlLadenDialog#10](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_1.cpp)]

1. Dodawanie obrazów opcjonalne dla każdego stanu możliwe: wybrane lub nonselected, a nakładki. Poniższy kod dodaje trzy obrazy wstępnie zdefiniowane.

     [!code-cpp[NVC_MFCControlLadenDialog#11](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_2.cpp)]

1. Skojarz listy obrazów z formantem z wywołaniem [CComboBoxEx::SetImageList](../mfc/reference/ccomboboxex-class.md#setimagelist).

Po listy obrazów został skojarzony z formantem, można określić osobno, obrazy, które każdy element użyje trzy stany. Aby uzyskać więcej informacji, zobacz [Ustawianie obrazów dla pojedynczego elementu](../mfc/setting-the-images-for-an-individual-item.md).

## <a name="see-also"></a>Zobacz też

[Korzystanie z CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

