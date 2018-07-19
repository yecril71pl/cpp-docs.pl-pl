---
title: Typy związane z obiektami interfejsu użytkownika | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.uiobject.msgs
dev_langs:
- C++
helpviewer_keywords:
- message types and user interface objects [MFC]
ms.assetid: 681ee1a7-f6e6-4ea0-9fc6-1fb53a35516e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b7ecc948910dd618f343134b0e9e3133539d9e1f
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335483"
---
# <a name="message-types-associated-with-user-interface-objects"></a>Typy komunikatów związane z obiektami interfejsu użytkownika
W poniższej tabeli przedstawiono typy obiektów, z którymi pracujesz, a typy komunikatów związane z nimi.  
  
### <a name="user-interface-objects-and-associated-messages"></a>Obiekty interfejsu użytkownika i skojarzone wiadomości  
  
|Identyfikator obiektu:|Komunikaty|  
|---------------|--------------|  
|Nazwa klasy, reprezentujący do okna nadrzędnego|Komunikaty Windows odpowiednimi [CWnd](../../mfc/reference/cwnd-class.md)-klasy pochodnej: okno dialogowe, okna, okno podrzędne, okno podrzędne MDI lub okno ramek najwyższego poziomu.|  
|Identyfikator menu lub klawiszy skrótów|— Komunikat polecenia (wykonuje funkcję program).<br />-UPDATE_COMMAND_UI komunikat (dynamicznie aktualizuje element menu).|  
|Identyfikator formantu|Komunikaty powiadomień dotyczących kontrolki dla typu wybranej kontrolki.|  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowanie komunikatów do funkcji](../../mfc/reference/mapping-messages-to-functions.md)   
 [Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)   
 [Dodawanie funkcji członkowskiej](../../ide/adding-a-member-function-visual-cpp.md)   
 [Dodawanie zmiennej członkowskiej](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Zastępowanie funkcji wirtualnych](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Handler komunikatów MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Nawigacja w strukturze klas](../../ide/navigating-the-class-structure-visual-cpp.md)
