---
title: Wirtualne formanty listy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e4891a4ccacf57dc43788bfa2a82decbe32961fb
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952830"
---
# <a name="virtual-list-controls"></a>Wirtualne kontrolki listy
Formant listy wirtualnej jest formantu widoku listy, który ma styl LVS_OWNERDATA. Ten styl umożliwia kontrolę do obsługi liczba elementów do **DWORD** (domyślna liczba elementów rozciąga się tylko do **int**). Jednak Największą zaletą udostępniane przez ten styl jest możliwość tylko podzbiór elementów danych w pamięci w dowolnym momencie. Dzięki temu formantu widoku listy wirtualnej do nadają się do użytku z dużych baz danych informacji, których konkretnych metod uzyskiwania dostępu do danych znajdują się już w miejscu.  
  
> [!NOTE]
>  Oprócz funkcji listy wirtualnej `CListCtrl`, MFC również zapewnia te same funkcje w [clistview —](../mfc/reference/clistview-class.md) klasy.  
  
 Istnieją pewne problemy ze zgodnością, które należy zwrócić uwagę przy opracowywaniu formantów listy wirtualnej. Aby uzyskać więcej informacji zobacz sekcję problemy ze zgodnością tematu kontrolki widok listy w zestawie Windows SDK.  
  
## <a name="handling-the-lvngetdispinfo-notification"></a>Obsługa powiadomienia LVN_GETDISPINFO  
 Wirtualne formanty listy Obsługa elementu bardzo niewielka ilość informacji. Z wyjątkiem Wybór elementu i informacje fokus informacje o wszystkich elementach jest zarządzana przez właściciela formantu. Framework za pomocą komunikatu powiadomienia LVN_GETDISPINFO żąda informacji. Aby Podaj wymagane informacje, właściciel kontrolki listy wirtualnej (lub formancie) musi obsługiwać tego powiadomienia. Można to łatwo zrobić przy użyciu okna właściwości (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)). Wynikowy kod powinien wyglądać jak w następującym przykładzie (gdzie `CMyDialog` jest właścicielem obiektu kontrolki listy wirtualnej i okno dialogowe obsługuje powiadomienia):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]  
  
 W obsłudze wiadomości LVN_GETDISPINFO powiadomienia musisz sprawdzić, aby zobaczyć, jakie rodzaje informacji jest wymagany. Możliwe wartości to:  
  
-   `LVIF_TEXT` *PszText* elementu członkowskiego musi być wypełnione.  
  
-   `LVIF_IMAGE` *IImage* elementu członkowskiego musi być wypełnione.  
  
-   `LVIF_INDENT` *IIndent* elementu członkowskiego musi być wypełnione.  
  
-   `LVIF_PARAM` *LParam* elementu członkowskiego musi być wypełnione. (Brak podelementów.)  
  
-   `LVIF_STATE` *Stanu* elementu członkowskiego musi być wypełnione.  
  
 Następnie należy określić, niezależnie od zażądane wstecz do struktury.  
  
 Poniższe (pobierane z treści funkcji obsługi powiadomień dla obiekt formantu listy) przedstawiono jeden sposób poprzez dostarczanie informacji dla buforów tekstu i obrazu elementu:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]  
  
## <a name="caching-and-virtual-list-controls"></a>Buforowania i wirtualne formanty listy  
 Ponieważ ten typ formantu listy jest przeznaczony dla dużych zestawów danych, zaleca się pamięci podręcznej danych żądanego elementu w celu zwiększenia wydajności pobierania. Framework zapewnia mechanizm podpowiedzi do pamięci podręcznej ułatwiających optymalizacji pamięci podręcznej, wysyłając powiadomienie LVN_ODCACHEHINT.  
  
 Poniższy przykład aktualizuje zakres przekazany do funkcji obsługi pamięci podręcznej.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]  
  
 Aby uzyskać więcej informacji na przygotowanie i obsługi pamięci podręcznej zobacz sekcję zarządzania pamięcią podręczną tematu kontrolki widok listy w zestawie Windows SDK.  
  
## <a name="finding-specific-items"></a>Znajdowanie określonych elementów  
 LVN_ODFINDITEM powiadomienie jest wysyłane przez formant listy wirtualnej konkretnego kontrolki elementu listy musi znajdować się. Jest wysyłany komunikat powiadomienia, kiedy kontrolka widoku listy otrzymuje szybki dostęp do klucza lub gdy otrzyma komunikat LVM_FINDITEM. Wyszukaj informacje są wysyłane w postaci **LVFINDINFO** struktury, która jest elementem członkowskim o **NMLVFINDITEM** struktury. Obsługa tego komunikatu przez zastąpienie `OnChildNotify` funkcja listy kontroli obiektu i wewnątrz treści program obsługi, sprawdź, czy komunikat LVN_ODFINDITEM. Jeśli znaleziono, wykonaj odpowiednią akcję.  
  
 Należy przygotować się, aby wyszukać elementu, który odpowiada informacje podane przez formantu widoku listy. Powinien zwrócić indeks elementu w przypadku powodzenia lub wartość -1, jeśli żadnego pasującego elementu zostanie znaleziony.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CListCtrl](../mfc/using-clistctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

