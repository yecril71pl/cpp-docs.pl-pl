---
title: Zapewnianie obsługi przeciągania i upuszczania w przypadku elementów nagłówka
ms.date: 11/04/2016
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
ms.openlocfilehash: 21ff14982baac93fac1cf3ee441353c079f4f760
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602972"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>Zapewnianie obsługi przeciągania i upuszczania w przypadku elementów nagłówka

Aby zapewnić obsługi przeciągania i upuszczania w przypadku elementów nagłówka, należy określić hds_dragdrop — styl. Obsługa przeciągania i upuszczania w przypadku elementów nagłówka zapewnia możliwości, aby zmienić kolejność elementów nagłówka kontrolki nagłówka. Domyślne zachowanie zawiera obraz półprzezroczystych przeciągania elementu nagłówka przeciąganie i wizualny wskaźnik informujący o nowe miejsce po przerwaniu elementu nagłówka.

Mającego typową funkcjonalność przeciągania i upuszczania, mogą rozszerzać domyślne zachowanie przeciągnij i upuść dzięki obsłudze HDN_BEGINDRAG i HDN_ENDDRAG powiadomienia. Można również dostosować wygląd obrazu przeciągania przez zastąpienie [CHeaderCtrl::CreateDragImage](../mfc/reference/cheaderctrl-class.md#createdragimage) funkcja elementu członkowskiego.

> [!NOTE]
>  Jeśli są Zapewnianie obsługi przeciągania i upuszczania, dla formantu osadzonego nagłówka w formancie listy, zobacz sekcję rozszerzone Style w [Zmienianie stylów kontrolki listy](../mfc/changing-list-control-styles.md) tematu.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)

