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
ms.openlocfilehash: 576735841748d0b99053d038f8d5f674d5692f00
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930192"
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>Przetwarzanie komunikatów powiadomień w formantach rozszerzonego pola kombi
Jak użytkownicy korzystają z pola kombi rozszerzonej, formantu (`CComboBoxEx`) wysyła komunikaty powiadomień do nadrzędnego okna, zazwyczaj obiekt widoku lub okna dialogowego. Obsługi tych wiadomości, jeśli chcesz zrobić coś w odpowiedzi. Na przykład gdy użytkownik aktywuje listy rozwijanej lub klika w polu edycji formantu, CBEN_BEGINEDIT powiadomienie jest wysyłane.  
  
 Okno właściwości można dodać obsługi powiadomień do klasy nadrzędnej dla tych wiadomości, które chcesz wdrożyć.  
  
 Poniższa lista zawiera opis różnych powiadomienia wysyłane przez formancie rozszerzonego pola kombi.  
  
-   CBEN_BEGINEDIT wysyłany, gdy użytkownik aktywuje listy rozwijanej lub kliknięciu w polu edycji formantu.  
  
-   CBEN_DELETEITEM wysyłany, gdy element został usunięty.  
  
-   CBEN_DRAGBEGIN wysyłany, gdy użytkownik rozpocznie przeciąganie obrazu elementu wyświetlanego edycji części kontrolki.  
  
-   CBEN_ENDEDIT wysyłany, gdy użytkownik zakończył operację w polu edycji lub został wybrany element z listy rozwijanej formantu.  
  
-   CBEN_GETDISPINFO wysyłane do pobrania wyświetlane informacje o elemencie wywołania zwrotnego.  
  
-   CBEN_INSERTITEM wysyłany, gdy nowy element został wstawiony w formancie.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Kontrolki](../mfc/controls-mfc.md)

