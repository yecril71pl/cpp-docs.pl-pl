---
title: Przetwarzanie komunikatów powiadomień w formancie paska pomocniczego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a06df0bdfe8d1b81b4285fc86378f3da99882698
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>Przetwarzanie komunikatów powiadomień w formancie paska pomocniczego
W klasie nadrzędnej formantu paska pomocniczego, Utwórz `OnChildNotify` funkcji obsługi z instrukcji switch dla każdego formantu paska pomocniczego (`CReBarCtrl`) komunikatów powiadomień, które mają być obsługiwane. Powiadomienia są wysyłane do okna nadrzędnego, gdy użytkownik przeciąga obiektów nad formantem paska pomocniczego, zmiany układu paskami pomocniczymi, usuwa paskami w formancie paska pomocniczego i tak dalej.  
  
 Następujące komunikaty powiadomienia mogą być wysyłane przez obiekt formantu paska pomocniczego:  
  
-   **RBN_AUTOSIZE** wysyłany przez kontrolkę paska pomocniczego (utworzone za pomocą **RBS_AUTOSIZE** styl) po paska pomocniczego automatycznie samodzielnie zmienia rozmiar.  
  
-   **RBN_BEGINDRAG** wysyłany przez kontrolkę paska pomocniczego, gdy użytkownik rozpocznie przeciąganie grupy.  
  
-   **RBN_CHILDSIZE** wysyłany przez kontrolkę paska pomocniczego, gdy zmieniany jest rozmiar okna podrzędnego pasma.  
  
-   **RBN_DELETEDBAND** wysyłany przez kontrolkę paska pomocniczego, po usunięciu grupy.  
  
-   **RBN_DELETINGBAND** wysyłany przez kontrolkę paska pomocniczego, gdy obiekt band ma zostać usunięty.  
  
-   **RBN_ENDDRAG** wysyłany przez kontrolkę paska pomocniczego, gdy użytkownik przestanie przeciągać grupy.  
  
-   **RBN_GETOBJECT** wysyłany przez kontrolkę paska pomocniczego (utworzone za pomocą **RBS_REGISTERDROP** styl) gdy obiekt zostanie przeciągnięty nad poza pasmem w formancie.  
  
-   **RBN_HEIGHTCHANGE** wysyłany przez kontrolkę paska pomocniczego, gdy zmieniono jego wysokość.  
  
-   **RBN_LAYOUTCHANGED** wysyłany przez kontrolkę paska pomocniczego, gdy użytkownik zmieni się układ pasm kontrolki.  
  
 Aby uzyskać więcej informacji o te powiadomienia, zobacz [odwołania formantu paska pomocniczego](http://msdn.microsoft.com/library/windows/desktop/bb774375) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

