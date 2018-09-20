---
title: Obraz informacji o listach obrazów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c98bc629cde74cf7a6fc8a416de862f50a1dd5ae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422288"
---
# <a name="image-information-in-image-lists"></a>Informacje o obrazach na listach obrazów

[CImageList](../mfc/reference/cimagelist-class.md) obejmuje pewną liczbę funkcji, które pobierać informacje z listy obrazów. [GetImageInfo](../mfc/reference/cimagelist-class.md#getimageinfo) funkcja elementu członkowskiego wypełnia `IMAGEINFO` strukturę z informacjami o pojedynczego obrazu, w tym obsługi obrazu i maska mapy bitowej, liczbę płaszczyzn kolorów i bity na piksel i prostokąt otaczający obraz mapy bitowej obrazu. Bezpośrednie manipulowanie mapy bitowe dla obrazu, można użyć tych informacji.

[Getimagecount —](../mfc/reference/cimagelist-class.md#getimagecount) funkcja elementu członkowskiego pobiera liczbę obrazów w listy obrazów.

Można utworzyć na podstawie obrazu i maska w listy obrazów za pomocą ikony [ExtractIcon](../mfc/reference/cimagelist-class.md#extracticon) funkcja elementu członkowskiego. Funkcja zwraca uchwyt ikonę nowego elementu.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CImageList](../mfc/using-cimagelist.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

