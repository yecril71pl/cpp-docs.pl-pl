---
title: Wirtualne kontrolki listy | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5544582d65d84e95a22e78c9d663902d7df2dd24
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436042"
---
# <a name="virtual-list-controls"></a>Wirtualne kontrolki listy

Kontrolki listy wirtualnej jest kontrolka widoku listy, którego styl LVS_OWNERDATA. Ten styl umożliwia kontrolowanie, które umożliwiają liczba elementów do **DWORD** (domyślna liczba elementów tylko rozszerza **int**). Jednak Największą zaletą udostępniane przez ten styl jest możliwość tylko podzbiór elementów danych w pamięci w dowolnym momencie. Dzięki temu kontrolkę widok listy wirtualnej przystosowany do użytku z dużych baz danych informacji, których konkretnych metod dostępu do danych znajdują się już w miejscu.

> [!NOTE]
>  Oprócz funkcji listy wirtualnej `CListCtrl`, biblioteka MFC zawiera również te same funkcje w [CListView](../mfc/reference/clistview-class.md) klasy.

Istnieją pewne problemy ze zgodnością, w których należy wiedzieć podczas tworzenia wirtualne kontrolki listy. Aby uzyskać więcej informacji zobacz sekcję problemy ze zgodnością w temacie kontrolki widok listy w zestawie Windows SDK.

## <a name="handling-the-lvngetdispinfo-notification"></a>Obsługa powiadomienia LVN_GETDISPINFO

Wirtualne kontrolki listy zachować informacje o elementach bardzo mała. Z wyjątkiem zaznaczenie elementu i informacji fokus wszystkie informacje o elementach odbywa się przez właściciela formantu. Zażądane przez platformę, za pośrednictwem LVN_GETDISPINFO komunikat z powiadomieniem. Aby podać wymagane informacje, właściciel kontrolki listy wirtualnej (lub samej kontrolce) musi obsługiwać tego powiadomienia. Można to łatwo zrobić w oknie właściwości (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)). Wynikowy kod powinien wyglądać podobnie jak w poniższym przykładzie (gdzie `CMyDialog` jest właścicielem obiektu kontrolki listy wirtualnej i okno dialogowe jest obsługa powiadomienia):

[!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]

W procedurze obsługi LVN_GETDISPINFO komunikat powiadomienia musisz sprawdzić, aby zobaczyć, jakie rodzaje informacji jest wymagana. Możliwe wartości to:

- `LVIF_TEXT` *PszText* elementu członkowskiego musi być wypełnione.

- `LVIF_IMAGE` *IImage* elementu członkowskiego musi być wypełnione.

- `LVIF_INDENT` *IIndent* elementu członkowskiego musi być wypełnione.

- `LVIF_PARAM` *LParam* elementu członkowskiego musi być wypełnione. (Brak elementów podrzędnych.)

- `LVIF_STATE` *Stanu* elementu członkowskiego musi być wypełnione.

Następnie należy określić, niezależnie od zażądane powrót do struktury.

Poniższy przykład (pobierane z treści obsługi powiadomień dla obiektu formantu listy) przedstawia jedną z możliwych metod poprzez dostarczanie informacji dla buforów tekst i obraz elementu:

[!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]

## <a name="caching-and-virtual-list-controls"></a>Buforowanie i wirtualne kontrolki listy

Ponieważ ten typ kontrolki listy jest przeznaczony dla dużych zestawów danych, zaleca się pamięci podręcznej danych żądanego elementu w celu zwiększenia wydajności pobierania. Struktura zapewnia mechanizm podpowiedzi do pamięci podręcznej, aby pomóc w optymalizacji pamięci podręcznej, wysyłając powiadomienie LVN_ODCACHEHINT.

Poniższy przykład aktualizuje pamięć podręczną z zakresem przekazany do funkcji programu obsługi.

[!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]

Aby uzyskać więcej informacji na temat przygotowywania i obsługi pamięci podręcznej zobacz sekcję zarządzanie pamięcią podręczną tematu kontrolki widok listy w zestawie Windows SDK.

## <a name="finding-specific-items"></a>Znajdowanie określonych elementów

LVN_ODFINDITEM komunikatu powiadomienia są wysyłane przez kontrolki listy wirtualnej, gdy element formantu listy określonego musi ma zostać odnaleziona. Komunikat powiadomienia są wysyłane, gdy kontrolka widoku listy otrzymuje szybki dostęp do klucza lub po odebraniu wiadomości LVM_FINDITEM. Wyszukaj informacje są wysyłane w postaci **LVFINDINFO** struktury, która jest elementem członkowskim o **NMLVFINDITEM** struktury. Obsługa tego komunikatu przez zastąpienie `OnChildNotify` funkcji listy kontrolować obiektu i wewnątrz treści programu obsługi, sprawdź, czy komunikat LVN_ODFINDITEM. Jeśli znaleziono, wykonaj odpowiednią akcję.

Należy być przygotowanym do wyszukiwania elementu, który odpowiada informacje podane przez kontrolkę widok listy. Powinien zwrócić indeks elementu w przypadku powodzenia lub wartość -1, jeśli żadnego pasującego elementu zostanie znaleziony.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

