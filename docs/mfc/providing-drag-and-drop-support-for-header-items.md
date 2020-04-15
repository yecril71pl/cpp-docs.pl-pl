---
title: Zapewnianie obsługi przeciągania i upuszczania w przypadku elementów nagłówka
ms.date: 11/04/2016
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
ms.openlocfilehash: 8dfaabf3da62c216d3da662f59c57b63e695d9ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371164"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>Zapewnianie obsługi przeciągania i upuszczania w przypadku elementów nagłówka

Aby zapewnić obsługę przeciągania i upuszczania elementów nagłówka, określ styl HDS_DRAGDROP. Obsługa przeciągania i upuszczania elementów nagłówka umożliwia użytkownikowi ponowne kolejność elementów nagłówka formantu nagłówka. Domyślne zachowanie zapewnia półprzezroczysty obraz przeciągania elementu nagłówka i wizualny wskaźnik nowej pozycji, jeśli element nagłówka zostanie upuszczony.

Podobnie jak w przypadku typowych funkcji przeciągania i upuszczania, można rozszerzyć domyślne zachowanie przeciągania i upuszczania, obsługując powiadomienia HDN_BEGINDRAG i HDN_ENDDRAG. Wygląd przeciągania można również dostosować, zastępując funkcję elementu członkowskiego [CHeaderCtrl::CreateDragImage.](../mfc/reference/cheaderctrl-class.md#createdragimage)

> [!NOTE]
> Jeśli w formancie listy zapewniasz obsługę przeciągania i upuszczania, zobacz sekcję Styl rozszerzony w temacie [Zmienianie stylów sterowania listą.](../mfc/changing-list-control-styles.md)

## <a name="see-also"></a>Zobacz też

[Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)
