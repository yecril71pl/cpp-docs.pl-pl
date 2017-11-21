---
title: "Zapewnianie obsługi przeciągania i upuszczania w przypadku elementów nagłówka | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a6f9d305786fa54231deae3dcd65624ba39875e0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>Zapewnianie obsługi przeciągania i upuszczania w przypadku elementów nagłówka
Aby zapewnić obsługę przeciągania i upuszczania w przypadku elementów nagłówka, określ `HDS_DRAGDROP` stylu. Obsługi przeciągania i upuszczania w przypadku elementów nagłówka umożliwia użytkownika można zmienić kolejność elementów nagłówka formantu nagłówka. Domyślne zachowanie zawiera obraz półprzezroczystych przeciągania przeciąganie elementu nagłówka i wizualnej nowego położenia po przerwaniu elementu nagłówka.  
  
 Zgodnie z typowych funkcji przeciągania i upuszczania, można rozszerzyć domyślne zachowanie przeciągania i upuszczania Obsługa **HDN_BEGINDRAG** i **HDN_ENDDRAG** powiadomienia. Można również dostosować wygląd obrazu, przeciągnij przez zastąpienie [CHeaderCtrl::CreateDragImage](../mfc/reference/cheaderctrl-class.md#createdragimage) funkcję elementu członkowskiego.  
  
> [!NOTE]
>  Jeśli są Zapewnianie obsługi przeciągania i upuszczania formantu osadzonego nagłówka w formancie listy, zobacz sekcję rozszerzone Style w [Zmienianie stylów formantu listy](../mfc/changing-list-control-styles.md) tematu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)

