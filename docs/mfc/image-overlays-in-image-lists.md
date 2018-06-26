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
ms.openlocfilehash: 93d37b49a949ab29e0ae888d9c961da086ee4ca4
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928599"
---
# <a name="image-overlays-in-image-lists"></a>Nakładki obrazów na listach obrazów
Każdy listy obrazów ([CImageList](../mfc/reference/cimagelist-class.md)) zawiera listę obrazów do użycia jako maski nakładki. "Maska nakładki" jest rysowany jako przezroczysty za pośrednictwem innego obrazu obrazu. Żadnego obrazu może służyć jako maska nakładki. Można określić maksymalnie cztery maski nakładki na listy obrazów.  
  
 Dodaj indeks obrazu do listy maski nakładki za pomocą [SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) funkcji członkowskiej, indeks obrazu i indeks maski nakładki. Należy pamiętać, że indeksy masek nakładki są oparte na jeden zamiast liczony od zera.  
  
 Rysuj maski nakładki nad obrazu przy użyciu jednego wywołania `Draw`. Parametry zawierają indeks obrazu do rysowania i indeksu maski nakładki. Należy użyć [INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408) makra, aby określić indeks maska nakładki. Można również określić obrazu nakładki podczas wywoływania metody [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect) funkcję elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CImageList](../mfc/using-cimagelist.md)   
 [Kontrolki](../mfc/controls-mfc.md)

