---
title: Programy obsługi dla poleceń i powiadomień dotyczących formantu karty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- commands [MFC], handlers for
- functions [MFC], handler
- handlers [MFC]
- controls [MFC], notifications
- handlers [MFC], control notification [MFC]
- notifications [MFC], handlers for control
- handlers [MFC], command
ms.assetid: 20f57f4a-f577-4c09-80a2-43faf32a1c2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bda42393cd55b60ab787665b51957bb2f94c5df3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430085"
---
# <a name="handlers-for-commands-and-control-notifications"></a>Programy obsługi dla poleceń i powiadomień dotyczących formantów

Nie ma żadnych domyślne programy obsługi poleceń i komunikatów powiadamianie kontrolki. W związku z tym są powiązane tylko przez Konwencję nazewnictwa inne programy obsługi dla tych kategorii wiadomości. Kiedy mapujesz powiadomień polecenia lub formantu do obsługi systemu windows właściwości proponuje nazwę na podstawie kodu Identyfikatora lub kontroli powiadomień polecenia. Można zaakceptować proponowana nazwa, zmienić lub zamień go.

Konwencja sugeruje nazwę procedury obsługi w obu kategoriach obiektu interfejsu użytkownika, które reprezentują. Dlatego program obsługi poleceń Wytnij menu Edycja może mieć nazwę.

[!code-cpp[NVC_MFCMessageHandling#4](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_1.h)]

Ponieważ polecenie Cut tak często jest zaimplementowana w aplikacji, platformę powoduje wstępne definiowanie identyfikator polecenia dla polecenia Wytnij jako **id_edit_cut —**. Aby uzyskać listę wszystkich poleceń wstępnie zdefiniowane identyfikatory Zobacz plik AFXRES. H. Aby uzyskać więcej informacji, zobacz [standardowych poleceń](../mfc/standard-commands.md).

Ponadto Konwencji sugeruje funkcję obsługi **BN_CLICKED** komunikatu powiadomienia przy użyciu przycisku z etykietą "Moja-Button" może mieć nazwę.

[!code-cpp[NVC_MFCMessageHandling#5](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_2.h)]

To polecenie może przypisywać identyfikator **IDC_MY_BUTTON** , ponieważ jest to równoważne do obiektu interfejsu użytkownika specyficznych dla aplikacji.

Obie kategorie komunikatów nie przyjmują argumentów i zwraca żadnej wartości.

## <a name="see-also"></a>Zobacz też

[Deklarowanie funkcji obsługi komunikatów](../mfc/declaring-message-handler-functions.md)
