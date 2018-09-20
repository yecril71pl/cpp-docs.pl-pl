---
title: Zapewnianie obsługi przeciągania i upuszczania w przypadku elementów nagłówka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b2eaa5040d34a442868a8fa6cb9f2aae08b0a6f3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407702"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>Zapewnianie obsługi przeciągania i upuszczania w przypadku elementów nagłówka

Aby zapewnić obsługi przeciągania i upuszczania w przypadku elementów nagłówka, należy określić hds_dragdrop — styl. Obsługa przeciągania i upuszczania w przypadku elementów nagłówka zapewnia możliwości, aby zmienić kolejność elementów nagłówka kontrolki nagłówka. Domyślne zachowanie zawiera obraz półprzezroczystych przeciągania elementu nagłówka przeciąganie i wizualny wskaźnik informujący o nowe miejsce po przerwaniu elementu nagłówka.

Mającego typową funkcjonalność przeciągania i upuszczania, mogą rozszerzać domyślne zachowanie przeciągnij i upuść dzięki obsłudze HDN_BEGINDRAG i HDN_ENDDRAG powiadomienia. Można również dostosować wygląd obrazu przeciągania przez zastąpienie [CHeaderCtrl::CreateDragImage](../mfc/reference/cheaderctrl-class.md#createdragimage) funkcja elementu członkowskiego.

> [!NOTE]
>  Jeśli są Zapewnianie obsługi przeciągania i upuszczania, dla formantu osadzonego nagłówka w formancie listy, zobacz sekcję rozszerzone Style w [Zmienianie stylów kontrolki listy](../mfc/changing-list-control-styles.md) tematu.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)

