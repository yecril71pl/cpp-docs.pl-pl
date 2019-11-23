---
title: Tworzenie niemodalnego arkusza właściwości
ms.date: 11/04/2016
helpviewer_keywords:
- modeless property sheets
- property sheets, modeless
- Create method [MFC], property sheets
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
ms.openlocfilehash: 90f6dcd5659d308a4b39d6a7d5a42003fc1f2111
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685688"
---
# <a name="creating-a-modeless-property-sheet"></a>Tworzenie niemodalnego arkusza właściwości

Zwykle tworzone arkusze właściwości będą modalne. W przypadku korzystania z modalnego arkusza właściwości użytkownik musi zamknąć arkusz właściwości przed użyciem innej części aplikacji. W tym artykule opisano metody, których można użyć do utworzenia niemodalnego arkusza właściwości, który umożliwia użytkownikowi zachowanie otwartego arkusza właściwości podczas korzystania z innych części aplikacji.

Aby wyświetlić arkusz właściwości jako niemodalne okno dialogowe zamiast jako modalne okno dialogowe, wywołaj [CPropertySheet:: Create](../mfc/reference/cpropertysheet-class.md#create) zamiast [DoModal](../mfc/reference/cpropertysheet-class.md#domodal). Należy również zaimplementować pewne dodatkowe zadania w celu obsługi niemodalnego arkusza właściwości.

Jedno z dodatkowych zadań polega na wymianie danych między arkuszem właściwości i obiektem zewnętrznym, który jest modyfikowany, gdy arkusz właściwości jest otwarty. Jest to na ogół takie samo zadanie jak w przypadku standardowych okien dialogowych niemodalnych. Częścią tego zadania jest implementacja kanału komunikacji między niemodalnym arkuszem właściwości a obiektem zewnętrznym, do którego mają zastosowanie ustawienia właściwości. Ta implementacja jest znacznie łatwiejsza, jeśli pochodna jest Klasa z [CPropertySheet](../mfc/reference/cpropertysheet-class.md) dla niemodalnego arkusza właściwości. W tym artykule przyjęto założenie, że zostało to zrobione.

Jedna metoda komunikacji między niemodalnym arkuszem właściwości a obiektem zewnętrznym (na przykład bieżący wybór w widoku) polega na zdefiniowaniu wskaźnika z arkusza właściwości do obiektu zewnętrznego. Zdefiniuj funkcję (o nazwie "`SetMyExternalObject`") w klasie pochodnej `CPropertySheet`, aby zmienić wskaźnik zawsze, gdy fokus zmieni się z jednego obiektu zewnętrznego na inny. Funkcja `SetMyExternalObject` musi zresetować ustawienia dla każdej strony właściwości, aby odzwierciedlić nowo wybrany obiekt zewnętrzny. Aby to osiągnąć, funkcja `SetMyExternalObject` musi mieć możliwość uzyskania dostępu do obiektów [CPropertyPage](../mfc/reference/cpropertypage-class.md) należących do klasy `CPropertySheet`.

Najbardziej wygodnym sposobem zapewnienia dostępu do stron właściwości w arkuszu właściwości jest osadzenie `CPropertyPage` obiektów w obiekcie pochodnym `CPropertySheet`. Osadzenie `CPropertyPage` obiektów w obiekcie pochodnym `CPropertySheet`różni się od typowego projektu dla modalnych okien dialogowych, gdzie właściciel arkusza właściwości tworzy obiekty `CPropertyPage` i przekazuje je do arkusza właściwości za pośrednictwem [CPropertySheet:: AddPage](../mfc/reference/cpropertysheet-class.md#addpage).

Istnieje wiele alternatywnych interfejsów użytkownika do określania, kiedy ustawienia niemodalnego arkusza właściwości mają być stosowane do obiektu zewnętrznego. Alternatywą jest zastosowanie ustawień bieżącej strony właściwości zawsze wtedy, gdy użytkownik zmieni dowolną wartość. Kolejną alternatywą jest udostępnienie przycisku Zastosuj, który umożliwia użytkownikowi gromadzenie zmian na stronach właściwości przed przekazaniem ich do obiektu zewnętrznego. Aby uzyskać informacje na temat sposobów obsługi przycisku Zastosuj, zobacz artykuł [obsługa przycisku Zastosuj](../mfc/handling-the-apply-button.md).

## <a name="see-also"></a>Zobacz także

[Arkusze właściwości](../mfc/property-sheets-mfc.md)<br/>
[Wymiana danych](../mfc/exchanging-data.md)<br/>
[Praca z polami okna dialogowego w MFC](../mfc/life-cycle-of-a-dialog-box.md)
