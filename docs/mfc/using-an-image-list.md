---
title: Używanie list obrazów
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
ms.openlocfilehash: 710831ea8ef6b52292ba3e8eb84a69575c6c7508
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226831"
---
# <a name="using-an-image-list"></a>Używanie list obrazów

Typowym użyciem listy obrazów jest Poniższy wzorzec:

- Utwórz obiekt [Korzystanie CImageList](../mfc/reference/cimagelist-class.md) i Wywołaj jedno z przeciążeń funkcji [Create](../mfc/reference/cimagelist-class.md#create) , aby utworzyć listę obrazów i dołączyć ją do `CImageList` obiektu.

- Jeśli nie dodano obrazów podczas tworzenia listy obrazów, Dodaj obrazy do listy obrazów przez wywołanie funkcji [Dodaj](../mfc/reference/cimagelist-class.md#add) lub [Odczytaj](../mfc/reference/cimagelist-class.md#read) składową.

- Skojarz listę obrazów z kontrolką, wywołując odpowiednią funkcję elementu członkowskiego tej kontrolki lub Rysuj obrazy z listy obrazów samodzielnie przy użyciu funkcji elementu członkowskiego [rysowania](../mfc/reference/cimagelist-class.md#draw) listy obrazów.

- Prawdopodobnie użytkownik może przeciągać obraz przy użyciu wbudowanej obsługi przeciągania z listy obrazów.

> [!NOTE]
> Jeśli lista obrazów została utworzona przy użyciu **`new`** operatora, należy zniszczyć `CImageList` obiekt po wykonaniu tej czynności.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CImageList](../mfc/using-cimagelist.md)<br/>
[Formanty](../mfc/controls-mfc.md)
