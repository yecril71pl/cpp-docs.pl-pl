---
title: Nakładki obrazów na listach obrazów
ms.date: 11/04/2016
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
ms.openlocfilehash: ec795193a28a68d8aee61e9932481a89c4b3e8e0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508385"
---
# <a name="image-overlays-in-image-lists"></a>Nakładki obrazów na listach obrazów

Każda lista obrazów ([Korzystanie CImageList](../mfc/reference/cimagelist-class.md)) zawiera listę obrazów do użycia jako maski nakładki. "Maska nakładki" to obraz rysowany w sposób przezroczysty na innym obrazie. Dowolny obraz może być używany jako maska nakładki. Można określić maksymalnie cztery maski nakładania na listę obrazów.

Indeks obrazu można dodać do listy masek nakładki przy użyciu funkcji składowej [SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) , indeksu obrazu oraz indeksu maski nakładki. Należy zauważyć, że indeksy dla masek nakładki są oparte na jednym, a nie na podstawie zera.

Narysujmy maskę nakładki na obrazie przy użyciu jednego `Draw`wywołania do. Parametry obejmują indeks obrazu do rysowania i indeks maski nakładki. Aby określić indeks maski nakładki, należy użyć makra [INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask) . Możesz również określić obraz nakładki podczas wywoływania funkcji składowej [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect) .

## <a name="see-also"></a>Zobacz także

[Korzystanie z CImageList](../mfc/using-cimagelist.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
