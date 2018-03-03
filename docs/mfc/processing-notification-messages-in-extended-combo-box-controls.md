---
title: "Przetwarzanie komunikatów powiadomień w rozszerzonych formantów pola kombi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a78e7b9fd8f9c67f14a4bb51088866785d372cca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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

