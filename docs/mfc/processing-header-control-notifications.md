---
title: Przetwarzanie powiadomień dotyczących formantów nagłówka | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 539e7411dcc47be17bb10a5322e30a524679ca8c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194214"
---
# <a name="processing-header-control-notifications"></a>Przetwarzanie powiadomień dotyczących formantu karty
W klasie widoku lub w oknie dialogowym, użyj okna właściwości, aby utworzyć [OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) funkcji obsługi za pomocą instrukcji switch dla każdego formantu nagłówka ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) komunikaty powiadomień, które mają być Obsługa (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)). Powiadomienia są wysyłane do okna nadrzędnego, gdy użytkownik kliknie przycisk lub kliknie dwukrotnie element nagłówka drags na linię podziału między elementami i tak dalej.  
  
 Powiadomienia związane z formantem nagłówka są wymienione w [odwołanie do formantu nagłówka](https://msdn.microsoft.com/library/windows/desktop/bb775239) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

