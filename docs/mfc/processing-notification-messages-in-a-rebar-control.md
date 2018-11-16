---
title: Przetwarzanie komunikatów powiadomień w formancie paska pomocniczego
ms.date: 11/04/2016
helpviewer_keywords:
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
ms.openlocfilehash: 4c35a1efb1c93aecf17e8f57b9e96c033aa4334a
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693187"
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>Przetwarzanie komunikatów powiadomień w formancie paska pomocniczego

W klasie nadrzędnej formantu paska pomocniczego, Utwórz `OnChildNotify` funkcji obsługi za pomocą instrukcji switch dla każdego formantu paska pomocniczego (`CReBarCtrl`) komunikaty powiadomień, które mają być obsługiwane. Powiadomienia są wysyłane do okna nadrzędnego, gdy użytkownik przeciągnie obiektów nad kontrolką paska pomocniczego, zmiany układu paskami usuwa paskami w formancie paska pomocniczego i tak dalej.

Następujące powiadomienia mogą być wysyłane przez obiekt formantu paska pomocniczego:

- Wysyłany przez kontrolkę paska pomocniczego (utworzonej przy użyciu stylu RBS_AUTOSIZE), RBN_AUTOSIZE po paska pomocniczego automatycznie zmienia rozmiar samego.

- RBN_BEGINDRAG wysyłany przez kontrolkę paska pomocniczego, gdy użytkownik rozpoczyna, przeciągając obiekt band.

- RBN_CHILDSIZE wysyłany przez kontrolkę paska pomocniczego, gdy zmieniany jest rozmiar okna podrzędnego pasma.

- RBN_DELETEDBAND wysyłany przez kontrolkę paska pomocniczego, po usunięciu poza pasmem.

- RBN_DELETINGBAND wysyłany przez kontrolkę paska pomocniczego, gdy ma zostać usunięty poza pasmem.

- RBN_ENDDRAG wysyłany przez kontrolkę paska pomocniczego, gdy użytkownik zatrzymuje, przeciągając obiekt band.

- RBN_GETOBJECT wysyłany przez kontrolkę paska pomocniczego (utworzonej przy użyciu stylu RBS_REGISTERDROP), gdy obiekt jest przeciągany nad pasma w formancie.

- RBN_HEIGHTCHANGE wysyłany przez kontrolkę paska pomocniczego, gdy zmieniono jego wysokość.

- RBN_LAYOUTCHANGED wysyłany przez kontrolkę paska pomocniczego, gdy użytkownik zmienia układ pasm kontrolki.

Aby uzyskać więcej informacji na temat tych powiadomień, zobacz [odwołanie do formantu paska pomocniczego](/windows/desktop/controls/rebar-control-reference) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

