---
title: "Obsługa przycisku Zastosuj | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Apply button in property sheet
- property sheets, Apply button
ms.assetid: 7e977015-59b8-406f-b545-aad0bfd8d55b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d72186d3b3d29613007291396aa07ba4060a726a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="handling-the-apply-button"></a>Obsługa przycisku Zastosuj
Arkusze właściwości mają możliwość, która nie w standardowych oknach dialogowych: umożliwiają one użytkownika zastosować zmiany wprowadzone przed zamknięciem arkusza właściwości. Jest to realizowane za pomocą przycisku Zastosuj. W tym artykule omówiono metody, których można użyć, aby prawidłowo zaimplementować tę funkcję.  
  
 Modalne okna dialogowe zwykle dotyczą ustawienia obiektu zewnętrznego, gdy użytkownik kliknie przycisk OK, aby zamknąć okno dialogowe. To samo dotyczy arkusz właściwości: gdy użytkownik kliknie przycisk OK, nowe ustawienia w arkuszu właściwości zostały zastosowane.  
  
 Jednak można zezwolić użytkownikowi na Zapisz ustawienia bez konieczności zamknąć okno dialogowe właściwości arkusza. Jest to funkcja przycisk Zastosuj. Przycisk Zastosuj stosuje ustawienia bieżącego we wszystkich stron właściwości w obiekcie zewnętrznych, w przeciwieństwie do stosowania tylko bieżące ustawienia aktualnie aktywnej strony.  
  
 Domyślnie jest zawsze wyłączona przycisk Zastosuj. Należy napisać kod, aby uaktywnić przycisk Zastosuj w odpowiednim czasie, a następnie należy napisać kod do implementacji efekt Zastosuj, co zostało opisane poniżej.  
  
 Jeśli nie chcesz, aby oferować funkcjonalność Zastosuj do użytkownika, nie jest konieczne do usunięcia przycisku Zastosuj. Możesz pozostawić ją wyłączoną, jak będą wspólne dla aplikacji używających standardowego właściwości arkusza pomocy technicznej w przyszłych wersjach systemu Windows.  
  
 Aby zgłosić strony jako zmodyfikowane i Włącz przycisk Zastosuj, należy wywołać **CPropertyPage::SetModified (PRAWDA)**. Jeśli jedna z raportu strony są modyfikowane, przycisk Zastosuj pozostanie włączony, niezależnie od tego, czy został zmodyfikowany aktualnie aktywnej strony.  
  
 Należy wywołać [CPropertyPage::SetModified](../mfc/reference/cpropertypage-class.md#setmodified) zawsze, gdy użytkownik zmieni wszystkie ustawienia na stronie. Jednym ze sposobów Wykryj, kiedy użytkownik zmienia ustawienie na stronie jest do zaimplementowania programy obsługi powiadomień zmiany dla każdej kontrolki na stronie właściwości, takie jak **EN_CHANGE** lub **BN_CLICKED**.  
  
 Aby zaimplementować efekt przycisk Zastosuj, arkusz właściwości należy wskazać jego właściciela lub zewnętrznych obiektów w aplikacji, aby zastosować bieżące ustawienia na stronach właściwości. W tym samym czasie, arkusz właściwości należy wyłączyć przycisk Zastosuj, wywołując **CPropertyPage::SetModified (FALSE)** dla wszystkich stron, które stosowane ich modyfikacje w obiekcie zewnętrznym.  
  
 Na przykład tego procesu, zobacz przykład ogólne MFC [PROPDLG](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Arkusze właściwości](../mfc/property-sheets-mfc.md)

