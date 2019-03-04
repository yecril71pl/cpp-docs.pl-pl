---
title: Informacje o obrazach na listach obrazów
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
ms.openlocfilehash: 7b83b7e5f7de6f8ccca95d732f71a5d73a97e943
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263068"
---
# <a name="image-information-in-image-lists"></a>Informacje o obrazach na listach obrazów

[CImageList](../mfc/reference/cimagelist-class.md) obejmuje pewną liczbę funkcji, które pobierać informacje z listy obrazów. [GetImageInfo](../mfc/reference/cimagelist-class.md#getimageinfo) funkcja elementu członkowskiego wypełnia `IMAGEINFO` strukturę z informacjami o pojedynczego obrazu, w tym obsługi obrazu i maska mapy bitowej, liczbę płaszczyzn kolorów i bity na piksel i prostokąt otaczający obraz mapy bitowej obrazu. Bezpośrednie manipulowanie mapy bitowe dla obrazu, można użyć tych informacji.

[Getimagecount —](../mfc/reference/cimagelist-class.md#getimagecount) funkcja elementu członkowskiego pobiera liczbę obrazów w listy obrazów.

Można utworzyć na podstawie obrazu i maska w listy obrazów za pomocą ikony [ExtractIcon](../mfc/reference/cimagelist-class.md#extracticon) funkcja elementu członkowskiego. Funkcja zwraca uchwyt ikonę nowego elementu.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CImageList](../mfc/using-cimagelist.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
