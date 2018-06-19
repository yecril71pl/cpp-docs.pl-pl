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
ms.openlocfilehash: 55a55a6e015a2f8c1613a85717c030737712c4da
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345410"
---
# <a name="image-overlays-in-image-lists"></a>Nakładki obrazów na listach obrazów
Każdy listy obrazów ([CImageList](../mfc/reference/cimagelist-class.md)) zawiera listę obrazów do użycia jako maski nakładki. "Maska nakładki" jest rysowany jako przezroczysty za pośrednictwem innego obrazu obrazu. Żadnego obrazu może służyć jako maska nakładki. Można określić maksymalnie cztery maski nakładki na listy obrazów.  
  
 Dodaj indeks obrazu do listy maski nakładki za pomocą [SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) funkcji członkowskiej, indeks obrazu i indeks maski nakładki. Należy pamiętać, że indeksy masek nakładki są oparte na jeden zamiast liczony od zera.  
  
 Rysuj maski nakładki na obrazie przy użyciu jednego wywołania do **rysowania**. Parametry zawierają indeks obrazu do rysowania i indeksu maski nakładki. Należy użyć [INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408) makra, aby określić indeks maska nakładki. Można również określić obrazu nakładki podczas wywoływania metody [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect) funkcję elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CImageList](../mfc/using-cimagelist.md)   
 [Kontrolki](../mfc/controls-mfc.md)

