---
title: "Zapewnianie obsługi przeciągania i upuszczania w przypadku elementów nagłówka | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fd1ac2171a13610ee3aeabed12f5348089a57491
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>Zapewnianie obsługi przeciągania i upuszczania w przypadku elementów nagłówka
Aby zapewnić obsługę przeciągania i upuszczania w przypadku elementów nagłówka, określ `HDS_DRAGDROP` stylu. Obsługi przeciągania i upuszczania w przypadku elementów nagłówka umożliwia użytkownika można zmienić kolejność elementów nagłówka formantu nagłówka. Domyślne zachowanie zawiera obraz półprzezroczystych przeciągania przeciąganie elementu nagłówka i wizualnej nowego położenia po przerwaniu elementu nagłówka.  
  
 Zgodnie z typowych funkcji przeciągania i upuszczania, można rozszerzyć domyślne zachowanie przeciągania i upuszczania Obsługa **HDN_BEGINDRAG** i **HDN_ENDDRAG** powiadomienia. Można również dostosować wygląd obrazu, przeciągnij przez zastąpienie [CHeaderCtrl::CreateDragImage](../mfc/reference/cheaderctrl-class.md#createdragimage) funkcję elementu członkowskiego.  
  
> [!NOTE]
>  Jeśli są Zapewnianie obsługi przeciągania i upuszczania formantu osadzonego nagłówka w formancie listy, zobacz sekcję rozszerzone Style w [Zmienianie stylów formantu listy](../mfc/changing-list-control-styles.md) tematu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)

