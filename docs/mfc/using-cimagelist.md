---
title: Korzystanie z CImageList
ms.date: 11/04/2016
helpviewer_keywords:
- image list control
- CImageList class [MFC], using
ms.assetid: 3d2a909e-d641-46b7-aada-81cab1a29b41
ms.openlocfilehash: 09fd0e95ce2981afbebbfe10d87b26f88a7b5e13
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447223"
---
# <a name="using-cimagelist"></a>Korzystanie z CImageList

Lista obrazów reprezentowana przez klasę [Korzystanie CImageList](../mfc/reference/cimagelist-class.md)jest kolekcją obrazów o takim samym rozmiarze, z których każdy może być określony przez jego indeks. Listy obrazów służą do wydajnego zarządzania dużymi zestawami ikon lub map bitowych. Listy obrazów nie są same dla kontrolek, ponieważ nie są oknami. są one jednak używane z kilkoma różnymi typami kontrolek, w tym formantami list ([CListCtrl](../mfc/reference/clistctrl-class.md)), kontrolkami drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) i kontrolkami kart ([CTabCtrl](../mfc/reference/ctabctrl-class.md)).

Wszystkie obrazy na liście obrazów są zawarte w jednej, szerokiej mapie bitowej w formacie urządzenia ekranowego. Lista obrazów może również zawierać mapę bitową monochromatyczny, która zawiera maski używane do rysowania obrazów w sposób przezroczysty (styl ikon). `CImageList` udostępnia funkcje członkowskie, które umożliwiają rysowanie obrazów, tworzenie i niszczenie list obrazów, Dodawanie i usuwanie obrazów, zastępowanie obrazów, scalanie obrazów i przeciąganie obrazów.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Typy list obrazów](../mfc/types-of-image-lists.md)

- [Używanie list obrazów](../mfc/using-an-image-list.md)

- [Operowanie listami obrazów](../mfc/manipulating-image-lists.md)

- [Rysowanie obrazów z poziomu listy obrazów](../mfc/drawing-images-from-an-image-list.md)

- [Nakładki obrazów na listach obrazów](../mfc/image-overlays-in-image-lists.md)

- [Przeciąganie obrazów z listy obrazów](../mfc/dragging-images-from-an-image-list.md)

- [Informacje o obrazach na listach obrazów](../mfc/image-information-in-image-lists.md)

## <a name="see-also"></a>Zobacz też

[Kontrolki](../mfc/controls-mfc.md)
