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
ms.openlocfilehash: 6bf21021e204a6caf298453bab42db2aedff409c
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928423"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>Zapewnianie obsługi przeciągania i upuszczania w przypadku elementów nagłówka
Aby zapewnić obsługę przeciągania i upuszczania w przypadku elementów nagłówka, określ hds_dragdrop — styl. Obsługi przeciągania i upuszczania w przypadku elementów nagłówka umożliwia użytkownika można zmienić kolejność elementów nagłówka formantu nagłówka. Domyślne zachowanie zawiera obraz półprzezroczystych przeciągania przeciąganie elementu nagłówka i wizualnej nowego położenia po przerwaniu elementu nagłówka.  
  
 Jako z typowych funkcji przeciągania i upuszczania, można rozszerzyć domyślne zachowanie przeciągania i upuszczania dzięki obsłudze HDN_BEGINDRAG i HDN_ENDDRAG powiadomienia. Można również dostosować wygląd obrazu, przeciągnij przez zastąpienie [CHeaderCtrl::CreateDragImage](../mfc/reference/cheaderctrl-class.md#createdragimage) funkcję elementu członkowskiego.  
  
> [!NOTE]
>  Jeśli są Zapewnianie obsługi przeciągania i upuszczania formantu osadzonego nagłówka w formancie listy, zobacz sekcję rozszerzone Style w [Zmienianie stylów formantu listy](../mfc/changing-list-control-styles.md) tematu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)

