---
title: "Przetwarzanie komunikatów powiadomień w formantach listy | Dokumentacja firmy Microsoft"
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
- processing notifications [MFC]
- CListCtrl class [MFC], processing notifications
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2c4a900b6fe0741de852c15afca37a974fc3e989
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="processing-notification-messages-in-list-controls"></a>Przetwarzanie komunikatów powiadomień w kontrolkach listy
Użytkownik kliknie przycisk nagłówki kolumn, przeciągnij ikony, Edytuj etykiety i tak dalej, kontrolki listy ([CListCtrl](../mfc/reference/clistctrl-class.md)) wysyła komunikaty powiadomień do jej okna nadrzędnego. Obsługi tych wiadomości, jeśli chcesz zrobić coś w odpowiedzi. Na przykład gdy użytkownik kliknie nagłówek kolumny, można posortować elementy na podstawie zawartości klikniętej kolumnę, tak jak Microsoft Outlook.  
  
 Proces **WM_NOTIFY** wiadomości z kontrolki listy w klasie widoku lub okna dialogowego. Okno właściwości do utworzenia [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) funkcji obsługi z instrukcji switch oparte na komunikat powiadomienia, które jest obsługiwane.  
  
 Lista powiadomień formant listy można wysyłać do jej okna nadrzędnego, zobacz [odwołania formantu widoku listy](http://msdn.microsoft.com/library/windows/desktop/bb774737) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CListCtrl](../mfc/using-clistctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

