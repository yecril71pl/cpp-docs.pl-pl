---
title: "Przetwarzanie komunikatów powiadomień dotyczących formantu karty | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- notifications [MFC], tab controls
- CTabCtrl class [MFC], processing notifications
- notifications [MFC], processing in CTabCtrl
- processing notifications [MFC]
- tab controls [MFC], processing notifications
ms.assetid: 758ccb7a-9e73-48f8-9073-23f7cb09918c
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 840ff6fc5dd47a2059e62608b5a5d6f231f8f17c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="processing-tab-control-notification-messages"></a>Przetwarzanie komunikatów powiadomień dotyczących formantu karty
Użytkownik kliknie przycisk karty lub przyciski, formantu karty ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) wysyła komunikaty powiadomień do jej okna nadrzędnego. Obsługi tych wiadomości, jeśli chcesz zrobić coś w odpowiedzi. Na przykład gdy użytkownik kliknie kartę, warto ustawień kontroli danych na stronie przed wyświetleniem go.  
  
 Proces **WM_NOTIFY** komunikaty z formantu karty w klasie widoku lub okna dialogowego. Okno właściwości do utworzenia [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) funkcji obsługi z instrukcji switch oparte na komunikat powiadomienia, które jest obsługiwane. Lista powiadomień formantu karty można wysyłać do jej okna nadrzędnego, zobacz **powiadomienia** sekcji [odwołanie do formantu karty](http://msdn.microsoft.com/library/windows/desktop/bb760548) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTabCtrl](../mfc/using-ctabctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

