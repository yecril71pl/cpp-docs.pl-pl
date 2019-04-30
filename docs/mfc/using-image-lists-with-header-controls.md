---
title: Używanie list obrazów z formantami nagłówka
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
ms.openlocfilehash: 3d9a4a0c655fa46c15d8c4d9b2b4e90cd34c2937
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411542"
---
# <a name="using-image-lists-with-header-controls"></a>Używanie list obrazów z formantami nagłówka

Elementy nagłówka mają możliwość wyświetlania obrazu w elemencie nagłówka. Ten obraz przechowywane na liście powiązanego obrazu jest 16 x 16 pikseli i ma takie same charakterystyki jak obrazy ikon używanych w kontrolka widoku listy. Aby można było pomyślnie zaimplementować to zachowanie, musi najpierw utworzyć i zainicjować listy obrazów, skojarzenia listy z formantem nagłówka i zmodyfikowanie atrybutów elementu nagłówek, który wyświetla obraz.

Poniższa procedura przedstawia szczegółowe informacje, za pomocą wskaźnika do formantu nagłówka (`m_pHdrCtrl`) i wskaźnik do listy obrazów (`m_pHdrImages`).

### <a name="to-display-an-image-in-a-header-item"></a>Aby wyświetlić obraz w element nagłówka

1. Utworzenia nowej listy obrazów (lub użyj istniejącego obiektu listy obrazu) przy użyciu [CImageList](../mfc/reference/cimagelist-class.md) konstruktora, przechowywania wynikowego wskaźnika.

1. Inicjowanie nowy obiekt listy obrazów, wywołując [CImageList::Create](../mfc/reference/cimagelist-class.md#create). Poniższy kod jest przykładem tego wywołania.

   [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]

1. Dodawanie obrazów dla każdego elementu nagłówka. Poniższy kod dodaje dwa obrazy wstępnie zdefiniowane.

   [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]

1. Skojarz listy obrazów z formantem nagłówka z wywołaniem [CHeaderCtrl::SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist).

1. Zmodyfikuj element nagłówka, aby wyświetlić obraz z listy skojarzony obraz. W poniższym przykładzie przypisano pierwszy obraz z `m_phdrImages`, do pierwszego elementu nagłówka `m_pHdrCtrl`.

   [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]

Aby uzyskać szczegółowe informacje na podstawie wartości parametru używany, zapoznaj się z odpowiednich [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md).

> [!NOTE]
>  Istnieje możliwość mają wiele formantów przy użyciu tej samej listy obrazów. Na przykład w standardowych kontrolka widoku listy, może istnieć obraz listy (16 x 16 pikseli obrazów) używane przez widoku małych ikon kontrolki widoku listy i elementy nagłówka kontrolki widoku listy.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)
