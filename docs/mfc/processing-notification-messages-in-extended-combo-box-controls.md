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
ms.openlocfilehash: b1e71502f818321dc8893f89f21993c25b032602
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>Przetwarzanie komunikatów powiadomień w formantach rozszerzonego pola kombi
Jak użytkownicy korzystają z pola kombi rozszerzonej, formantu (`CComboBoxEx`) wysyła komunikaty powiadomień do nadrzędnego okna, zazwyczaj obiekt widoku lub okna dialogowego. Obsługi tych wiadomości, jeśli chcesz zrobić coś w odpowiedzi. Na przykład gdy użytkownik aktywuje listy rozwijanej lub pole tekstowe kliknięć w formancie **CBEN_BEGINEDIT** powiadomienie jest wysyłane.  
  
 Okno właściwości można dodać obsługi powiadomień do klasy nadrzędnej dla tych wiadomości, które chcesz wdrożyć.  
  
 Poniższa lista zawiera opis różnych powiadomienia wysyłane przez formancie rozszerzonego pola kombi.  
  
-   **CBEN_BEGINEDIT** wysyłany, gdy użytkownik aktywuje listy rozwijanej lub polu edycji kliknięć w formancie.  
  
-   **CBEN_DELETEITEM** wysyłany, gdy element został usunięty.  
  
-   **CBEN_DRAGBEGIN** wysyłany, gdy użytkownik rozpocznie przeciąganie obrazu elementu wyświetlanego edycji części kontrolki.  
  
-   **CBEN_ENDEDIT** wysyłany, gdy użytkownik zakończył operację w polu edycji lub został wybrany element z listy rozwijanej formantu.  
  
-   **CBEN_GETDISPINFO** wysyłane do pobrania wyświetlane informacje o elemencie wywołania zwrotnego.  
  
-   **CBEN_INSERTITEM** wysyłany, gdy nowy element został wstawiony w formancie.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Kontrolki](../mfc/controls-mfc.md)

