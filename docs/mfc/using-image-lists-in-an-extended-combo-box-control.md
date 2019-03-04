---
title: Używanie list obrazów w formancie rozszerzonego pola kombi
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], combo boxes
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: dfff25fe-af70-47a2-8032-3901d1e6842d
ms.openlocfilehash: 6e4d983d53e49fc8d9c80c206f1a23078eb82f61
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266994"
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

## <a name="see-also"></a>Zobacz także

[Korzystanie z CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
