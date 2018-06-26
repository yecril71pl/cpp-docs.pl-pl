---
title: Przetwarzanie komunikatów powiadomień w formantach listy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- processing notifications [MFC]
- CListCtrl class [MFC], processing notifications
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5412bbf1fcb7e139394b9563965244080e5c179
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932084"
---
# <a name="processing-notification-messages-in-list-controls"></a>Przetwarzanie komunikatów powiadomień w kontrolkach listy
Użytkownik kliknie przycisk nagłówki kolumn, przeciągnij ikony, Edytuj etykiety i tak dalej, kontrolki listy ([CListCtrl](../mfc/reference/clistctrl-class.md)) wysyła komunikaty powiadomień do jej okna nadrzędnego. Obsługi tych wiadomości, jeśli chcesz zrobić coś w odpowiedzi. Na przykład gdy użytkownik kliknie nagłówek kolumny, można posortować elementy na podstawie zawartości klikniętej kolumnę, tak jak Microsoft Outlook.  
  
 Przetwarzaj wiadomości WM_NOTIFY z kontrolki listy w klasie widoku lub okna dialogowego. Okno właściwości do utworzenia [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) funkcji obsługi z instrukcji switch oparte na komunikat powiadomienia, które jest obsługiwane.  
  
 Lista powiadomień formant listy można wysyłać do jej okna nadrzędnego, zobacz [odwołania formantu widoku listy](http://msdn.microsoft.com/library/windows/desktop/bb774737) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CListCtrl](../mfc/using-clistctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

