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
ms.openlocfilehash: dce09e84e9a2b5262d05847746f819a122ec36c5
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208978"
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>Przetwarzanie komunikatów powiadomień w formancie paska pomocniczego
W klasie nadrzędnej formantu paska pomocniczego, Utwórz `OnChildNotify` funkcji obsługi za pomocą instrukcji switch dla każdego formantu paska pomocniczego (`CReBarCtrl`) komunikaty powiadomień, które mają być obsługiwane. Powiadomienia są wysyłane do okna nadrzędnego, gdy użytkownik przeciągnie obiektów nad kontrolką paska pomocniczego, zmiany układu paskami usuwa paskami w formancie paska pomocniczego i tak dalej.  
  
 Następujące powiadomienia mogą być wysyłane przez obiekt formantu paska pomocniczego:  
  
-   Wysyłany przez kontrolkę paska pomocniczego (utworzonej przy użyciu stylu RBS_AUTOSIZE), RBN_AUTOSIZE po paska pomocniczego automatycznie zmienia rozmiar samego.  
  
-   RBN_BEGINDRAG wysyłany przez kontrolkę paska pomocniczego, gdy użytkownik rozpoczyna, przeciągając obiekt band.  
  
-   RBN_CHILDSIZE wysyłany przez kontrolkę paska pomocniczego, gdy zmieniany jest rozmiar okna podrzędnego pasma.  
  
-   RBN_DELETEDBAND wysyłany przez kontrolkę paska pomocniczego, po usunięciu poza pasmem.  
  
-   RBN_DELETINGBAND wysyłany przez kontrolkę paska pomocniczego, gdy ma zostać usunięty poza pasmem.  
  
-   RBN_ENDDRAG wysyłany przez kontrolkę paska pomocniczego, gdy użytkownik zatrzymuje, przeciągając obiekt band.  
  
-   RBN_GETOBJECT wysyłany przez kontrolkę paska pomocniczego (utworzonej przy użyciu stylu RBS_REGISTERDROP), gdy obiekt jest przeciągany nad pasma w formancie.  
  
-   RBN_HEIGHTCHANGE wysyłany przez kontrolkę paska pomocniczego, gdy zmieniono jego wysokość.  
  
-   RBN_LAYOUTCHANGED wysyłany przez kontrolkę paska pomocniczego, gdy użytkownik zmienia układ pasm kontrolki.  
  
 Aby uzyskać więcej informacji na temat tych powiadomień, zobacz [odwołanie do formantu paska pomocniczego](https://msdn.microsoft.com/library/windows/desktop/bb774375) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

