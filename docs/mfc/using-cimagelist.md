---
title: Korzystanie z CImageList | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CImageList
dev_langs: C++
helpviewer_keywords:
- image list control
- CImageList class [MFC], using
ms.assetid: 3d2a909e-d641-46b7-aada-81cab1a29b41
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5db9ede8dc87fcb6b32eb825efed3e028872b6ff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="using-cimagelist"></a>Korzystanie z CImageList
Listy obrazów, reprezentowany przez klasę [CImageList](../mfc/reference/cimagelist-class.md), to zbiór tego samego rozmiaru obrazów, z których każdy może być przywoływane przez jej indeks. Listy obrazów umożliwiają wydajne zarządzanie dużymi zbiorami ikony lub mapy bitowe. Listy obrazów są same nie formantów, ponieważ nie są one windows; jednak są używane z kilkoma różnymi typami formantów, w tym kontrolki listy ([CListCtrl](../mfc/reference/clistctrl-class.md)), kontrolki drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) i na karcie formantów ([CTabCtrl](../mfc/reference/ctabctrl-class.md)).  
  
 Wszystkie obrazy na liście obrazów znajdują się w jednej, szeroki mapy bitowej w formacie ekranu urządzenia. Listy obrazów mogą również obejmować monochromatyczny mapy bitowej zawierającego maski używany do rysowania obrazów w sposób niewidoczny dla użytkownika (styl ikony). `CImageList`udostępnia funkcje Członkowskie, które umożliwiają rysowanie obrazów, tworzenie i zniszczyć listy obrazów, dodawanie i usuwanie obrazów, Zastąp obrazów, scalanie obrazów i przeciągnij obrazów.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Typy list obrazów](../mfc/types-of-image-lists.md)  
  
-   [Używanie List obrazów](../mfc/using-an-image-list.md)  
  
-   [Operowanie listami obrazów](../mfc/manipulating-image-lists.md)  
  
-   [Rysowanie obrazów z poziomu listy obrazów](../mfc/drawing-images-from-an-image-list.md)  
  
-   [Nakładki obrazów na listach obrazów](../mfc/image-overlays-in-image-lists.md)  
  
-   [Przeciąganie obrazów z listy obrazów](../mfc/dragging-images-from-an-image-list.md)  
  
-   [Informacje o obrazach na listach obrazów](../mfc/image-information-in-image-lists.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty](../mfc/controls-mfc.md)

