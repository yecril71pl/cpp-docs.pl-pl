---
title: Nakładki obrazów na listach obrazów
ms.date: 11/04/2016
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
ms.openlocfilehash: 8dd0b30ef29a48ebc763564e6fe23632cd300831
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262782"
---
# <a name="image-overlays-in-image-lists"></a>Nakładki obrazów na listach obrazów

Każdy z listy obrazów ([CImageList](../mfc/reference/cimagelist-class.md)) zawiera listę obrazów do użycia jako nakładka maski. "Maska nakładki" jest obrazem rysowane w sposób niewidoczny dla użytkownika za pośrednictwem innego obrazu. Dowolny obraz może służyć jako maski nakładki. Można określić maksymalnie cztery maski nakładki na listy obrazów.

Dodaj indeks obrazu do listy maski nakładki przy użyciu [SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) funkcja elementu członkowskiego, indeks obrazu i indeks maski nakładki. Należy pamiętać, że indeksy masek nakładki są oparte na jeden, a nie od zera.

Rysowanie maski nakładki na obrazie za pomocą jednego wywołania do `Draw`. Parametry zawierają indeks obrazu do rysowania i indeks maski nakładki. Należy użyć [INDEXTOOVERLAYMASK](/windows/desktop/api/commctrl/nf-commctrl-indextooverlaymask) makra, aby określić indeks maska nakładki. Należy również wskazać obraz nakładki podczas wywoływania [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect) funkcja elementu członkowskiego.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CImageList](../mfc/using-cimagelist.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
