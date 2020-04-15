---
title: Używanie list obrazów z formantami nagłówka
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
ms.openlocfilehash: 8002c16d1cdf5e0683b642001409b6da9c260660
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366474"
---
# <a name="using-image-lists-with-header-controls"></a>Używanie list obrazów z formantami nagłówka

Elementy nagłówka mają możliwość wyświetlania obrazu w elemencie nagłówka. Ten obraz, przechowywany na skojarzonej liście obrazów, ma 16 x 16 pikseli i ma takie same właściwości jak obrazy ikon używane w formancie widoku listy. Aby pomyślnie zaimplementować to zachowanie, należy najpierw utworzyć i zainicjować listę obrazów, skojarzyć listę z formantu nagłówka, a następnie zmodyfikować atrybuty elementu nagłówka, który wyświetli obraz.

Poniższa procedura ilustruje szczegóły za pomocą wskaźnika do formantu nagłówka (`m_pHdrCtrl`) i wskaźnika do listy obrazów (`m_pHdrImages`).

### <a name="to-display-an-image-in-a-header-item"></a>Aby wyświetlić obraz w elemencie nagłówka

1. Skonstruuj nową listę obrazów (lub użyj istniejącego obiektu listy obrazów) przy użyciu konstruktora [CImageList,](../mfc/reference/cimagelist-class.md) przechowując wynikowy wskaźnik.

1. Inicjowanie nowego obiektu listy obrazów przez [wywołanie CImageList::Create](../mfc/reference/cimagelist-class.md#create). Poniższy kod jest jednym z przykładów tego wywołania.

   [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]

1. Dodaj obrazy dla każdego elementu nagłówka. Poniższy kod dodaje dwa wstępnie zdefiniowane obrazy.

   [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]

1. Skojarz listę obrazów z formantem nagłówka z wywołaniem [CHeaderCtrl::SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist).

1. Zmodyfikuj element nagłówka, aby wyświetlić obraz z listy skojarzonych obrazów. Poniższy przykład przypisuje pierwszy obraz, z `m_phdrImages`, do `m_pHdrCtrl`pierwszego elementu nagłówka, .

   [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]

Szczegółowe informacje na temat zastosowano wartości parametrów, można znaleźć w odpowiednich [cheaderctrl](../mfc/reference/cheaderctrl-class.md).

> [!NOTE]
> Istnieje możliwość wielu formantów przy użyciu tej samej listy obrazów. Na przykład w formancie widoku listy standardowej może istnieć lista obrazów (obrazów o rozmiarze 16 x 16 pikseli) używana zarówno przez mały widok ikony formantu widoku listy, jak i elementy nagłówka formantu widoku listy.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)
