---
title: Typy skojarzone z obiektami interfejsu użytkownika | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 14a2309556ca6c5204247ccbe916aebe472a1da1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373427"
---
# <a name="message-types-associated-with-user-interface-objects"></a>Typy komunikatów związane z obiektami interfejsu użytkownika
W poniższej tabeli przedstawiono typy obiektów, z którymi pracujesz, a typy komunikatów skojarzonych z nimi.  
  
### <a name="user-interface-objects-and-associated-messages"></a>Obiekty interfejsu użytkownika i skojarzone wiadomości  
  
|Identyfikator obiektu:|Komunikaty|  
|---------------|--------------|  
|Nazwa klasy reprezentujące okna nadrzędnego|Komunikaty systemu Windows są odpowiednie do [CWnd](../../mfc/reference/cwnd-class.md)-klasy: okno dialogowe, okna, okno podrzędne, podrzędnego okna MDI lub okna ramowego najwyższego poziomu.|  
|Identyfikator menu lub klawiszy skrótów|-   **POLECENIE** wiadomości (wykonuje funkcję program).<br />-   **UPDATE_COMMAND_UI** komunikat (dynamicznie aktualizuje element menu).|  
|Identyfikator formantu|Komunikaty powiadomień dotyczących formantu dla wybranego typu formantu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowanie komunikatów na funkcje](../../mfc/reference/mapping-messages-to-functions.md)   
 [Dodawanie funkcji z kreatorami kodów](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)   
 [Dodawanie funkcji członkowskiej](../../ide/adding-a-member-function-visual-cpp.md)   
 [Dodawanie zmiennej członkowskiej](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Zastępowanie funkcji wirtualnych](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Handler komunikatów MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Nawigacja w strukturze klas](../../ide/navigating-the-class-structure-visual-cpp.md)
