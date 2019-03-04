---
title: Programy obsługi dla poleceń i powiadomień dotyczących formantów
ms.date: 11/04/2016
helpviewer_keywords:
- commands [MFC], handlers for
- functions [MFC], handler
- handlers [MFC]
- controls [MFC], notifications
- handlers [MFC], control notification [MFC]
- notifications [MFC], handlers for control
- handlers [MFC], command
ms.assetid: 20f57f4a-f577-4c09-80a2-43faf32a1c2e
ms.openlocfilehash: 6c92660c67fa91c27bb094111cebfef57904cdc7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296699"
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

## <a name="see-also"></a>Zobacz także

[Deklarowanie funkcji obsługi komunikatów](../mfc/declaring-message-handler-functions.md)
