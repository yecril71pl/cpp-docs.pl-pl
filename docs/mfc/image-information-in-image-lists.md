---
title: Informacje o obrazach na listach obrazów
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
ms.openlocfilehash: c12198c769585763095d22b73d11f7af3c9d6fc0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624501"
---
# <a name="image-information-in-image-lists"></a>Informacje o obrazach na listach obrazów

[Korzystanie CImageList](reference/cimagelist-class.md) zawiera szereg funkcji, które pobierają informacje z listy obrazów. Funkcja członkowska [GetImageInfo](reference/cimagelist-class.md#getimageinfo) wypełnia `IMAGEINFO` strukturę informacjami o pojedynczym obrazie, w tym uchwyty mapy bitowej obrazu i maski, liczbę płaszczyzn kolorów i bitów na piksel oraz obwiednię obrazu w mapie bitowej obrazu. Te informacje służą do bezpośredniego manipulowania mapami bitowymi obrazu.

Funkcja członkowska [GetImageCount](reference/cimagelist-class.md#getimagecount) Pobiera liczbę obrazów z listy obrazów.

Można utworzyć ikonę opartą na obrazie i masce na liście obrazów przy użyciu funkcji składowej [ExtractIcon](reference/cimagelist-class.md#extracticon) . Funkcja zwraca uchwyt nowej ikony.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CImageList](using-cimagelist.md)<br/>
[Formanty](controls-mfc.md)
