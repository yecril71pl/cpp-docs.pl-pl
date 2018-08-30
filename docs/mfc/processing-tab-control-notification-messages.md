---
title: Przetwarzanie komunikatów powiadomień dotyczących formantu karty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], tab controls
- CTabCtrl class [MFC], processing notifications
- notifications [MFC], processing in CTabCtrl
- processing notifications [MFC]
- tab controls [MFC], processing notifications
ms.assetid: 758ccb7a-9e73-48f8-9073-23f7cb09918c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b43bd125c43a11703f020951464fdf97f0ab374c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215027"
---
# <a name="processing-tab-control-notification-messages"></a>Przetwarzanie komunikatów powiadomień dotyczących formantu karty
Użytkownik kliknie przycisk, karty lub przyciski, formantu karty ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) wysyła powiadomienia do okna nadrzędnego. Obsługiwać te komunikaty, jeśli chcesz zrobić coś w odpowiedzi. Na przykład gdy użytkownik kliknie kartę, można wstępnie ustawione dane formantu na stronie przed wyświetleniem go.  
  
 Przetwarzanie wiadomości WM_NOTIFY z kontrolki karty w klasie widoku lub w oknie dialogowym. Okno właściwości, aby utworzyć [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) funkcji obsługi za pomocą instrukcji switch oparte na komunikat powiadomienia, które jest obsługiwane. Aby uzyskać listę powiadomień formant karty można wysyłać do okna nadrzędnego, zobacz **powiadomienia** części [odniesienie do formantu karty](https://msdn.microsoft.com/library/windows/desktop/bb760548) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTabCtrl](../mfc/using-ctabctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

