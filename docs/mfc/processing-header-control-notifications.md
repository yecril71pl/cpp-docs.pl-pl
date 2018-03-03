---
title: "Przetwarzanie powiadomień dotyczących formantu karty | Dokumentacja firmy Microsoft"
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
- CHeaderCtrl class [MFC], processing notifications
- controls [MFC], header
- notifications [MFC], processing for CHeaderCtrl
- header controls [MFC], processing notifications
- header control notifications
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a442e6aadf7c91918cd523c29330e79c753b115c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="processing-header-control-notifications"></a>Przetwarzanie powiadomień dotyczących formantu karty
W klasie widoku lub okna dialogowego okno właściwości do utworzenia [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) funkcji obsługi z instrukcji switch dla każdego formantu nagłówka ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) chcesz komunikaty powiadomień Obsługa (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)). Powiadomienia są wysyłane do okna nadrzędnego, gdy użytkownik kliknie lub kliknie dwukrotnie element nagłówka drags a podziału między elementami i tak dalej.  
  
 Komunikaty powiadomień skojarzony z formantem nagłówka są wymienione w [odwołanie do formantu nagłówka](http://msdn.microsoft.com/library/windows/desktop/bb775239) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

