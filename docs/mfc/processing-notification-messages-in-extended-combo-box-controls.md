---
title: Przetwarzanie komunikatów powiadomień w formantach rozszerzonego pola kombi
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
ms.openlocfilehash: 58a7c5ec36807489d24014055c39775b4552be03
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620985"
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>Przetwarzanie komunikatów powiadomień w formantach rozszerzonego pola kombi

Gdy użytkownicy współpracują z rozszerzonym polem kombi, formant ( `CComboBoxEx` ) wysyła komunikaty powiadomień do okna nadrzędnego, zwykle widok lub obiekt okna dialogowego. Obsługuj te komunikaty, jeśli chcesz zrobić coś w odpowiedzi. Na przykład gdy użytkownik uaktywnia listę rozwijaną lub kliknie w polu edycji kontrolki, zostanie wysłane powiadomienie CBEN_BEGINEDIT.

Użyj [kreatora klas](reference/mfc-class-wizard.md) , aby dodać programy obsługi powiadomień do klasy nadrzędnej dla tych komunikatów, które mają zostać wdrożone.

Na poniższej liście opisano różne powiadomienia wysyłane przez formant rozszerzonego pola kombi.

- CBEN_BEGINEDIT wysyłany, gdy użytkownik uaktywnia listę rozwijaną lub kliknie w polu edycji kontrolki.

- CBEN_DELETEITEM wysyłany po usunięciu elementu.

- CBEN_DRAGBEGIN wysyłany, gdy użytkownik rozpocznie przeciąganie obrazu elementu wyświetlanego w części edycji kontrolki.

- CBEN_ENDEDIT wysyłany, gdy użytkownik zakończył operację w polu edycji lub zaznaczył element z listy rozwijanej kontrolki.

- CBEN_GETDISPINFO wysłana do pobrania informacji o elemencie wywołania zwrotnego.

- CBEN_INSERTITEM wysyłany po wstawieniu nowego elementu w kontrolce.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CComboBoxEx](using-ccomboboxex.md)<br/>
[Formanty](controls-mfc.md)
