---
title: Korzystanie z CImageList | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CImageList
dev_langs:
- C++
helpviewer_keywords:
- image list control
- CImageList class [MFC], using
ms.assetid: 3d2a909e-d641-46b7-aada-81cab1a29b41
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8dd30b21b1ec635c6d5b5f2f5c6c6d9eb6fc3fa7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385794"
---
# <a name="using-cimagelist"></a>Korzystanie z CImageList
Listy obrazów, reprezentowany przez klasę [CImageList](../mfc/reference/cimagelist-class.md), to zbiór tego samego rozmiaru obrazów, z których każdy może być przywoływane przez jej indeks. Listy obrazów umożliwiają wydajne zarządzanie dużymi zbiorami ikony lub mapy bitowe. Listy obrazów są same nie formantów, ponieważ nie są one windows; jednak są używane z kilkoma różnymi typami formantów, w tym kontrolki listy ([CListCtrl](../mfc/reference/clistctrl-class.md)), kontrolki drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) i na karcie formantów ([CTabCtrl](../mfc/reference/ctabctrl-class.md)).  
  
 Wszystkie obrazy na liście obrazów znajdują się w jednej, szeroki mapy bitowej w formacie ekranu urządzenia. Listy obrazów mogą również obejmować monochromatyczny mapy bitowej zawierającego maski używany do rysowania obrazów w sposób niewidoczny dla użytkownika (styl ikony). `CImageList` udostępnia funkcje Członkowskie, które umożliwiają rysowanie obrazów, tworzenie i zniszczyć listy obrazów, dodawanie i usuwanie obrazów, Zastąp obrazów, scalanie obrazów i przeciągnij obrazów.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Typy list obrazów](../mfc/types-of-image-lists.md)  
  
-   [Używanie list obrazów](../mfc/using-an-image-list.md)  
  
-   [Operowanie listami obrazów](../mfc/manipulating-image-lists.md)  
  
-   [Rysowanie obrazów z poziomu listy obrazów](../mfc/drawing-images-from-an-image-list.md)  
  
-   [Nakładki obrazów na listach obrazów](../mfc/image-overlays-in-image-lists.md)  
  
-   [Przeciąganie obrazów z listy obrazów](../mfc/dragging-images-from-an-image-list.md)  
  
-   [Informacje o obrazach na listach obrazów](../mfc/image-information-in-image-lists.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki](../mfc/controls-mfc.md)

