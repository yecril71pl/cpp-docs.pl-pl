---
title: Obsługa przycisku Zastosuj
ms.date: 11/04/2016
helpviewer_keywords:
- Apply button in property sheet
- property sheets, Apply button
ms.assetid: 7e977015-59b8-406f-b545-aad0bfd8d55b
ms.openlocfilehash: cd1254a31491e713513f0db0d4cf87baddd9bb23
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618615"
---
# <a name="handling-the-apply-button"></a>Obsługa przycisku Zastosuj

Arkusze właściwości mają możliwość, że standardowe okna dialogowe nie są: umożliwiają użytkownikowi zastosowanie zmian wprowadzonych przed zamknięciem arkusza właściwości. W tym celu należy użyć przycisku Zastosuj. W tym artykule omówiono metody, których można użyć w celu poprawnego zaimplementowania tej funkcji.

Modalne okna dialogowe zwykle stosują ustawienia do obiektu zewnętrznego, gdy użytkownik kliknie przycisk OK, aby zamknąć okno dialogowe. Ta sama wartość dotyczy arkusza właściwości: gdy użytkownik kliknie przycisk OK, nowe ustawienia w arkuszu właściwości zostaną zastosowane.

Można jednak zezwolić użytkownikowi na zapisywanie ustawień bez konieczności zamykania okna dialogowego arkusza właściwości. Jest to funkcja przycisku Zastosuj. Przycisk Zastosuj stosuje bieżące ustawienia we wszystkich stronach właściwości do obiektu zewnętrznego, w przeciwieństwie do zastosowania tylko bieżących ustawień aktualnie aktywnej strony.

Domyślnie przycisk Zastosuj jest zawsze wyłączony. Musisz napisać kod, aby włączyć przycisk Zastosuj w odpowiednim czasie, i musisz napisać kod, aby zaimplementować efekt zastosowania, jak wyjaśniono poniżej.

Jeśli nie chcesz oferować funkcji Zastosuj użytkownikowi, nie musisz usuwać przycisku Zastosuj. Można pozostawić ją wyłączoną, ponieważ będzie ona wspólna dla aplikacji, które używają standardowej obsługi arkusza właściwości dostępnych w przyszłych wersjach systemu Windows.

Aby zgłosić stronę jako modyfikowaną i włączyć przycisk Zastosuj, wywołaj polecenie `CPropertyPage::SetModified( TRUE )` . Jeśli dowolna ze stron raportu zostanie zmodyfikowana, przycisk Zastosuj pozostanie włączony, bez względu na to, czy aktualnie aktywna strona została zmodyfikowana.

Należy wywołać [CPropertyPage:: SetModified](reference/cpropertypage-class.md#setmodified) za każdym razem, gdy użytkownik zmieni wszystkie ustawienia na stronie. Jednym ze sposobów na wykrycie zmiany ustawienia na stronie jest zaimplementowanie programów obsługi powiadomień o zmianach dla każdej kontrolki na stronie właściwości, takiej jak **EN_CHANGE** lub **BN_CLICKED**.

Aby zaimplementować efekt przycisku Zastosuj, arkusz właściwości musi poinformować jego właściciela lub inny obiekt zewnętrzny w aplikacji, aby zastosować bieżące ustawienia na stronach właściwości. W tym samym czasie arkusz właściwości powinien wyłączyć przycisk Zastosuj, wywołując `CPropertyPage::SetModified( FALSE )` dla wszystkich stron, które stosowały modyfikacje do obiektu zewnętrznego.

Aby zapoznać się z przykładem tego procesu, zobacz Ogólne przykładowe [PROPDLG](../overview/visual-cpp-samples.md)MFC.

## <a name="see-also"></a>Zobacz też

[Arkusze właściwości](property-sheets-mfc.md)
