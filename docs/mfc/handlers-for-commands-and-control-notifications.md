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
ms.openlocfilehash: 43b6a517b680a5f6ff092337fbf3d90dd0115dd7
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907972"
---
# <a name="handlers-for-commands-and-control-notifications"></a>Programy obsługi dla poleceń i powiadomień dotyczących formantów

Brak domyślnych programów obsługi dla poleceń lub komunikatów kontroli sterowania. W związku z tym użytkownik jest powiązany tylko z konwencją nazewnictwa dla tych kategorii komunikatów. Podczas mapowania polecenia lub powiadomienia o kontrolce do procedury obsługi [Kreator klas](reference/mfc-class-wizard.md) proponuje nazwę na podstawie identyfikatora polecenia lub kodu powiadomienia kontroli. Możesz zaakceptować proponowaną nazwę, zmienić ją lub zastąpić.

Konwencja sugeruje, że programy obsługi nazw są używane w obu kategoriach dla obiektu interfejsu użytkownika, które reprezentują. W ten sposób program obsługi polecenia Wytnij w menu Edycja może być nazwany

[!code-cpp[NVC_MFCMessageHandling#4](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_1.h)]

Ponieważ polecenie Wytnij jest tak często zaimplementowane w aplikacjach, struktura wstępnie definiuje identyfikator polecenia dla polecenia wycinania jako **ID_EDIT_CUT**. Aby uzyskać listę wszystkich wstępnie zdefiniowanych identyfikatorów poleceń, zobacz plik plik AFXRES. C. Aby uzyskać więcej informacji, zobacz [standardowe polecenia](../mfc/standard-commands.md).

Ponadto Konwencja sugeruje procedurę obsługi dla komunikatu powiadomienia **BN_CLICKED** z przycisku oznaczonego "My Button" może mieć nazwę

[!code-cpp[NVC_MFCMessageHandling#5](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_2.h)]

Można przypisać to polecenie identyfikator **IDC_MY_BUTTON** , ponieważ jest on równoważny obiektowi interfejsu użytkownika określonego dla aplikacji.

Obie kategorie komunikatów nie przyjmują argumentów i nie zwracają żadnej wartości.

## <a name="see-also"></a>Zobacz także

[Deklarowanie funkcji obsługi komunikatów](../mfc/declaring-message-handler-functions.md)
