---
title: Przetwarzanie powiadomień dotyczących formantu karty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHeaderCtrl class [MFC], processing notifications
- controls [MFC], header
- notifications [MFC], processing for CHeaderCtrl
- header controls [MFC], processing notifications
- header control notifications
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1a0fe657089c33679cf8d18f95268a70335804c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="processing-header-control-notifications"></a>Przetwarzanie powiadomień dotyczących formantu karty
W klasie widoku lub okna dialogowego okno właściwości do utworzenia [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) funkcji obsługi z instrukcji switch dla każdego formantu nagłówka ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) chcesz komunikaty powiadomień Obsługa (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)). Powiadomienia są wysyłane do okna nadrzędnego, gdy użytkownik kliknie lub kliknie dwukrotnie element nagłówka drags a podziału między elementami i tak dalej.  
  
 Komunikaty powiadomień skojarzony z formantem nagłówka są wymienione w [odwołanie do formantu nagłówka](http://msdn.microsoft.com/library/windows/desktop/bb775239) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

