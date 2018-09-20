---
title: Obraz nakładki na listach obrazów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c4052e06fe8aae1d149c3c09e88715d8270b361
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426565"
---
# <a name="image-overlays-in-image-lists"></a>Nakładki obrazów na listach obrazów

Każdy z listy obrazów ([CImageList](../mfc/reference/cimagelist-class.md)) zawiera listę obrazów do użycia jako nakładka maski. "Maska nakładki" jest obrazem rysowane w sposób niewidoczny dla użytkownika za pośrednictwem innego obrazu. Dowolny obraz może służyć jako maski nakładki. Można określić maksymalnie cztery maski nakładki na listy obrazów.

Dodaj indeks obrazu do listy maski nakładki przy użyciu [SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) funkcja elementu członkowskiego, indeks obrazu i indeks maski nakładki. Należy pamiętać, że indeksy masek nakładki są oparte na jeden, a nie od zera.

Rysowanie maski nakładki na obrazie za pomocą jednego wywołania do `Draw`. Parametry zawierają indeks obrazu do rysowania i indeks maski nakładki. Należy użyć [INDEXTOOVERLAYMASK](/windows/desktop/api/commctrl/nf-commctrl-indextooverlaymask) makra, aby określić indeks maska nakładki. Należy również wskazać obraz nakładki podczas wywoływania [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect) funkcja elementu członkowskiego.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CImageList](../mfc/using-cimagelist.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

