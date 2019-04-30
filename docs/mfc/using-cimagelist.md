---
title: Korzystanie z CImageList
ms.date: 11/04/2016
f1_keywords:
- CImageList
helpviewer_keywords:
- image list control
- CImageList class [MFC], using
ms.assetid: 3d2a909e-d641-46b7-aada-81cab1a29b41
ms.openlocfilehash: c3e4cec75ce23beb2a617d672170f86c608ca0a2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411841"
---
# <a name="using-cimagelist"></a>Korzystanie z CImageList

Listy obrazów, reprezentowane przez klasę [CImageList](../mfc/reference/cimagelist-class.md), to zbiór tych samych obrazów, z których każdy może być przywoływane przez jej indeks. Listy obrazów są używane do efektywnego zarządzania dużymi zestawami ikony lub mapy bitowej. Obraz listy są same nie przetwarzają formantów, ponieważ nie są one windows; jednak są one używane przy użyciu kilku różnych typów formantów, w tym kontrolki listy ([CListCtrl](../mfc/reference/clistctrl-class.md)), kontrolki drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) i klawisz tab, formanty ([CTabCtrl](../mfc/reference/ctabctrl-class.md)).

Wszystkie obrazy w listy obrazów znajdują się w jednym, szeroki mapy bitowej w formacie ekranu urządzenia. Listy obrazów może również obejmować monochromatycznych map bitowych, zawierający maski używany do rysowania obrazów w sposób niewidoczny dla użytkownika (styl ikony). `CImageList` dostarcza funkcji elementów członkowskich, umożliwiające rysowanie obrazów, tworzenie i zniszcz list obrazów, dodawania i usuwania obrazów, Zastąp obrazów, scalanie obrazów oraz przeciągnąć obrazy.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Typy list obrazów](../mfc/types-of-image-lists.md)

- [Używanie list obrazów](../mfc/using-an-image-list.md)

- [Operowanie listami obrazów](../mfc/manipulating-image-lists.md)

- [Rysowanie obrazów z poziomu listy obrazów](../mfc/drawing-images-from-an-image-list.md)

- [Nakładki obrazów na listach obrazów](../mfc/image-overlays-in-image-lists.md)

- [Przeciąganie obrazów z listy obrazów](../mfc/dragging-images-from-an-image-list.md)

- [Informacje o obrazach na listach obrazów](../mfc/image-information-in-image-lists.md)

## <a name="see-also"></a>Zobacz także

[Kontrolki](../mfc/controls-mfc.md)
