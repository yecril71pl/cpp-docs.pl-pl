---
title: Przetwarzanie komunikatów powiadomień w formancie paska pomocniczego
ms.date: 11/04/2016
helpviewer_keywords:
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
ms.openlocfilehash: e1e1aaa5056b43f0dd23976fead94bc800163613
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625190"
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>Przetwarzanie komunikatów powiadomień w formancie paska pomocniczego

W klasie nadrzędnej formantu paska pomocniczego Utwórz `OnChildNotify` funkcję programu obsługi z instrukcją Switch dla wszystkich komunikatów powiadomień paska pomocniczego-Control ( `CReBarCtrl` ), które chcesz obsłużyć. Powiadomienia są wysyłane do okna nadrzędnego, gdy użytkownik przeciągnie obiekty przez formant paska pomocniczego, zmieni układ przedziałów paska pomocniczego, usunie grupy z formantu paska pomocniczego i tak dalej.

Obiekt sterowania paska pomocniczego może wysyłać następujące komunikaty powiadomień:

- RBN_AUTOSIZE wysyłany przez formant paska pomocniczego (utworzony przy użyciu stylu RBS_AUTOSIZE), gdy paska pomocniczego automatycznie zmienia rozmiar siebie.

- RBN_BEGINDRAG wysyłany przez kontrolkę paska pomocniczego, gdy użytkownik rozpocznie przeciąganie pasma.

- RBN_CHILDSIZE wysyłany przez kontrolkę paska pomocniczego, gdy zmieniany jest rozmiar okna podrzędnego pasma.

- RBN_DELETEDBAND wysyłany przez formant paska pomocniczego po usunięciu pasma.

- RBN_DELETINGBAND wysyłany przez formant paska pomocniczego, gdy pasmo ma zostać usunięte.

- RBN_ENDDRAG wysyłany przez formant paska pomocniczego, gdy użytkownik zatrzyma przeciąganie pasma.

- RBN_GETOBJECT wysyłany przez formant paska pomocniczego (utworzony przy użyciu stylu RBS_REGISTERDROP), gdy obiekt jest przeciągany nad pasmem w kontrolce.

- RBN_HEIGHTCHANGE wysyłany przez formant paska pomocniczego, gdy jego wysokość zmieniła się.

- RBN_LAYOUTCHANGED wysyłany przez kontrolkę paska pomocniczego, gdy użytkownik zmienia układ pasm formantu.

Aby uzyskać więcej informacji na temat tych powiadomień, zobacz [paska pomocniczego Control Reference](/windows/win32/controls/rebar-control-reference) w Windows SDK.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CReBarCtrl](using-crebarctrl.md)<br/>
[Formanty](controls-mfc.md)
