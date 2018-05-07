---
title: Obsługa komunikatów odbitych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handling [MFC], reflected messages
- reflected messages, handling
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05b5f62169d2b65010ec75ab8c8b5c30959b77b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="handling-reflected-messages"></a>Obsługa komunikatów odbitych
Odbicie umożliwia obsługi komunikatów dla formantu, takie jak wiadomości `WM_CTLCOLOR`, **WM_COMMAND**, i **WM_NOTIFY**, bezpośrednio w formancie. Dzięki temu formantu więcej niezależną i przenośną. Mechanizm współpracuje z formanty standardowe systemu Windows, a także z formantami ActiveX (wcześniej nazywanych formantów OLE).  
  
 Komunikat odbicia umożliwia ponowne użycie Twojej `CWnd`-klas pochodnych łatwiej. Odbicie działa za pośrednictwem wiadomości [CWnd::OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify), przy użyciu specjalnego **ON_XXX_REFLECT** wpisy mapy wiadomości: na przykład **ON_CTLCOLOR_REFLECT** i **On_control_reflect —**. [62 Uwaga techniczna](../mfc/tn062-message-reflection-for-windows-controls.md) odbicie wiadomości bardziej szczegółowo opisano.  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić  
  
-   [Dowiedz się więcej o odbicie wiadomości](../mfc/tn062-message-reflection-for-windows-controls.md)  
  
-   [Implementowanie odbicie komunikatu dla formantu wspólnego](../mfc/tn062-message-reflection-for-windows-controls.md)  
  
-   [Implementowanie odbicie komunikatu dla formantów ActiveX](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Deklarowanie funkcji obsługi komunikatów](../mfc/declaring-message-handler-functions.md)
