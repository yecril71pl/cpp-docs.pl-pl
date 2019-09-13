---
title: Przetwarzanie komunikatów powiadomień w formantach rozszerzonego pola kombi
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
ms.openlocfilehash: 044cef644f746f7cb70944805882bd8e2f2806b4
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908111"
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>Przetwarzanie komunikatów powiadomień w formantach rozszerzonego pola kombi

Gdy użytkownicy współpracują z rozszerzonym polem kombi, formant`CComboBoxEx`() wysyła komunikaty powiadomień do okna nadrzędnego, zwykle widok lub obiekt okna dialogowego. Obsługuj te komunikaty, jeśli chcesz zrobić coś w odpowiedzi. Na przykład gdy użytkownik uaktywnia listę rozwijaną lub kliknie w polu edycji kontrolki, zostanie wysłane powiadomienie CBEN_BEGINEDIT.

Użyj [kreatora klas](reference/mfc-class-wizard.md) , aby dodać programy obsługi powiadomień do klasy nadrzędnej dla tych komunikatów, które mają zostać wdrożone.

Na poniższej liście opisano różne powiadomienia wysyłane przez formant rozszerzonego pola kombi.

- CBEN_BEGINEDIT wysyłany, gdy użytkownik uaktywnia listę rozwijaną lub klika w polu edycji kontrolki.

- CBEN_DELETEITEM wysyłany, gdy element został usunięty.

- CBEN_DRAGBEGIN wysyłany, gdy użytkownik rozpoczyna przeciąganie obrazu elementu wyświetlanego w części edycji kontrolki.

- CBEN_ENDEDIT wysyłany, gdy użytkownik zakończył operację w polu edycji lub zaznaczył element z listy rozwijanej kontrolki.

- CBEN_GETDISPINFO wysyłany w celu pobrania informacji o elemencie wywołania zwrotnego.

- CBEN_INSERTITEM wysyłany po wstawieniu nowego elementu w kontrolce.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
