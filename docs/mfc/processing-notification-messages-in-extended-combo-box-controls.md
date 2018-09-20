---
title: Przetwarzanie komunikatów powiadomień w rozszerzonych formantów pola kombi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2ea37fb8724a6427e287f1ebef23344662dcb34
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382794"
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>Przetwarzanie komunikatów powiadomień w formantach rozszerzonego pola kombi

Jak użytkownicy korzystać z rozszerzonych kombi, kontrolki (`CComboBoxEx`) wysyła powiadomienia do okna nadrzędnego, zazwyczaj obiekt widoku lub w oknie dialogowym. Obsługiwać te komunikaty, jeśli chcesz zrobić coś w odpowiedzi. Na przykład gdy użytkownik aktywuje listy rozwijanej lub kliknie pole edycji formantu, CBEN_BEGINEDIT powiadomienie jest wysyłane.

Okno właściwości do dodania obsługi powiadomień do klasy nadrzędnej dla tych wiadomości, które chcesz wdrożyć.

Poniższa lista zawiera opis różnych powiadomień wysyłanych przez formantu rozszerzonego pola kombi.

- CBEN_BEGINEDIT wysyłany, gdy użytkownik aktywuje listy rozwijanej lub kliknie pole edycji kontrolki.

- CBEN_DELETEITEM wysyłany, gdy element został usunięty.

- CBEN_DRAGBEGIN wysyłany, gdy użytkownik rozpoczął przeciąganie obrazów elementu wyświetlanych w Edytuj części kontrolki.

- CBEN_ENDEDIT wysyłany, gdy użytkownik zakończył operację w polu edycji lub został wybrany element z listy rozwijanej formantu.

- CBEN_GETDISPINFO wysyłane do pobrania wyświetlanie informacji o elemencie wywołania zwrotnego.

- CBEN_INSERTITEM wysyłany, gdy nowy element został wstawiony w formancie.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

