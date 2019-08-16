---
title: Przetwarzanie komunikatów powiadomień w formancie paska pomocniczego
ms.date: 11/04/2016
helpviewer_keywords:
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
ms.openlocfilehash: 948990c8597c2ccdcec496252c6801c02a78cbf5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507957"
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>Przetwarzanie komunikatów powiadomień w formancie paska pomocniczego

W klasie nadrzędnej formantu paska pomocniczego Utwórz `OnChildNotify` funkcję programu obsługi z instrukcją Switch dla wszystkich komunikatów powiadomień paska pomocniczego-Control (`CReBarCtrl`), które chcesz obsłużyć. Powiadomienia są wysyłane do okna nadrzędnego, gdy użytkownik przeciągnie obiekty przez formant paska pomocniczego, zmieni układ przedziałów paska pomocniczego, usunie grupy z formantu paska pomocniczego i tak dalej.

Obiekt sterowania paska pomocniczego może wysyłać następujące komunikaty powiadomień:

- RBN_AUTOSIZE wysyłany przez formant paska pomocniczego (utworzony przy użyciu stylu RBS_AUTOSIZE), gdy paska pomocniczego automatycznie zmienia rozmiar siebie.

- RBN_BEGINDRAG wysyłany przez kontrolkę paska pomocniczego, gdy użytkownik rozpoczyna przeciąganie pasma.

- RBN_CHILDSIZE wysyłany przez kontrolkę paska pomocniczego, gdy zmieniany jest rozmiar okna podrzędnego pasma.

- RBN_DELETEDBAND wysyłany przez kontrolkę paska pomocniczego po usunięciu pasma.

- RBN_DELETINGBAND wysyłany przez kontrolkę paska pomocniczego, gdy pasmo ma zostać usunięte.

- RBN_ENDDRAG wysyłany przez kontrolkę paska pomocniczego, gdy użytkownik zatrzyma przeciąganie pasma.

- RBN_GETOBJECT wysyłany przez formant paska pomocniczego (utworzony przy użyciu stylu RBS_REGISTERDROP), gdy obiekt jest przeciągany nad pasmem w kontrolce.

- RBN_HEIGHTCHANGE wysyłany przez kontrolkę paska pomocniczego, gdy jej wysokość zmieniła się.

- RBN_LAYOUTCHANGED wysyłany przez kontrolkę paska pomocniczego, gdy użytkownik zmienia układ pasm formantu.

Aby uzyskać więcej informacji na temat tych powiadomień, zobacz [paska pomocniczego Control Reference](/windows/win32/controls/rebar-control-reference) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
