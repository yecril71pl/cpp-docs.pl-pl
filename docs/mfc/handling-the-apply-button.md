---
title: Obsługa przycisku Zastosuj
ms.date: 11/04/2016
helpviewer_keywords:
- Apply button in property sheet
- property sheets, Apply button
ms.assetid: 7e977015-59b8-406f-b545-aad0bfd8d55b
ms.openlocfilehash: 30ee549a334a684deeb4a845f2fc49ee8bbe11db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240590"
---
# <a name="handling-the-apply-button"></a>Obsługa przycisku Zastosuj

Arkusze właściwości mają pola standardowe okno dialogowe nie obsługują funkcji: Umożliwiają one użytkownika zastosować zmiany wprowadzone przed zamknięciem arkusza właściwości. Odbywa się przy użyciu przycisku Zastosuj. W tym artykule omówiono metody, których można użyć, aby prawidłowo zaimplementować tę funkcję.

Modalne okna dialogowe zwykle dotyczą ustawienia obiektu zewnętrznego, gdy użytkownik kliknie przycisk OK, aby zamknąć okno dialogowe. Dotyczy to także dla arkusza właściwości: Gdy użytkownik kliknie przycisk OK, nowe ustawienia w arkuszu właściwości zaczęły obowiązywać.

Jednak można zezwolić użytkownikowi, który można zapisać ustawień bez konieczności zamknąć okno dialogowe arkusza właściwości. To jest funkcja przycisku Zastosuj. Przycisk Zastosuj stosuje bieżące ustawienia we wszystkich stron właściwości do obiektu zewnętrznego w przeciwieństwie do stosowania tylko bieżące ustawienia aktualnie aktywnej strony.

Domyślnie jest zawsze wyłączona przycisku Zastosuj. Należy napisać kod, aby włączyć przycisk Zastosuj w odpowiednim czasie, a następnie należy napisać kod, aby zaimplementować efekt Zastosuj, co zostało opisane poniżej.

Jeśli użytkownik nie chce oferują funkcje Zastosuj do użytkownika, nie jest potrzebne do usunięcia przycisku Zastosuj. Możesz pozostawić ją wyłączoną, ponieważ będą wspólne dla aplikacji, które używają standardowych właściwości arkusza pomocy technicznej dostępne w kolejnych wersjach systemu Windows.

Na stronie jako zmodyfikowane raportu i włączyć przycisk Zastosuj, należy wywołać `CPropertyPage::SetModified( TRUE )`. Ewentualnej stron raportu jest modyfikowany, przycisk Zastosuj pozostanie włączony, niezależnie od tego, czy aktualnie aktywnej strony została zmodyfikowana.

Należy wywołać [CPropertyPage::SetModified](../mfc/reference/cpropertypage-class.md#setmodified) zawsze, gdy użytkownik zmienia wszelkie ustawienia na stronie. Jednym ze sposobów, aby wykryć, gdy użytkownik zmieni ustawienie na stronie jest do zaimplementowania programy obsługi powiadomień dotyczących zmian dla każdej kontrolki na stronie właściwości, takie jak **EN_CHANGE** lub **BN_CLICKED**.

Aby zaimplementować efekt przycisk Zastosuj, arkusz właściwości musisz poinformować jego właściciela lub innych zewnętrznych obiektów w aplikacji, aby zastosować bieżące ustawienia na stronach właściwości. W tym samym czasie arkusza właściwości należy wyłączyć przycisk Zastosuj, wywołując `CPropertyPage::SetModified( FALSE )` dla wszystkich stron, które stosowane ich modyfikacji obiektu zewnętrznego.

Na przykład ten proces Zobacz próbki MFC-ogólne [PROPDLG](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Zobacz także

[Arkusze właściwości](../mfc/property-sheets-mfc.md)
