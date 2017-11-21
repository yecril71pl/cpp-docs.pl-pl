---
title: "Obraz informacji na listach obrazów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 80e897ec79314abb2e77864e53d470e72f275a94
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="image-information-in-image-lists"></a>Informacje o obrazach na listach obrazów
[Cimagelist —](../mfc/reference/cimagelist-class.md) zawiera szereg funkcji, które służą do pobierania informacji z listy obrazów. [GetImageInfo](../mfc/reference/cimagelist-class.md#getimageinfo) wypełnia funkcji członkowskiej `IMAGEINFO` struktury z informacjami o pojedynczego obrazu, w tym uchwytów obrazu i maska mapy bitowe, liczba płaszczyzn kolorów i bitów na piksel i prostokąt ograniczający obraz mapy bitowej obrazu. Te informacje można użyć bezpośrednio manipulować mapy bitowe dla obrazu.  
  
 [GetImageCount](../mfc/reference/cimagelist-class.md#getimagecount) funkcji członkowskiej pobiera liczbę obrazów na liście obrazów.  
  
 Można utworzyć na podstawie obrazu i maska w listy obrazów za pomocą ikony [ExtractIcon](../mfc/reference/cimagelist-class.md#extracticon) funkcję elementu członkowskiego. Funkcja zwraca dojście ikonę Nowy.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CImageList](../mfc/using-cimagelist.md)   
 [Formanty](../mfc/controls-mfc.md)

