---
title: Tworzenie niemodalnego arkusza właściwości
ms.date: 11/04/2016
helpviewer_keywords:
- modeless property sheets
- property sheets, modeless
- Create method [MFC], property sheets
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
ms.openlocfilehash: 7a44d96adf0a25a401fbc2e561bd7d32758a37d2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617170"
---
# <a name="creating-a-modeless-property-sheet"></a>Tworzenie niemodalnego arkusza właściwości

Zwykle tworzone arkusze właściwości będą modalne. W przypadku korzystania z modalnego arkusza właściwości użytkownik musi zamknąć arkusz właściwości przed użyciem innej części aplikacji. W tym artykule opisano metody, których można użyć do utworzenia niemodalnego arkusza właściwości, który umożliwia użytkownikowi zachowanie otwartego arkusza właściwości podczas korzystania z innych części aplikacji.

Aby wyświetlić arkusz właściwości jako niemodalne okno dialogowe zamiast jako modalne okno dialogowe, wywołaj [CPropertySheet:: Create](reference/cpropertysheet-class.md#create) zamiast [DoModal](reference/cpropertysheet-class.md#domodal). Należy również zaimplementować pewne dodatkowe zadania w celu obsługi niemodalnego arkusza właściwości.

Jedno z dodatkowych zadań polega na wymianie danych między arkuszem właściwości i obiektem zewnętrznym, który jest modyfikowany, gdy arkusz właściwości jest otwarty. Jest to na ogół takie samo zadanie jak w przypadku standardowych okien dialogowych niemodalnych. Częścią tego zadania jest implementacja kanału komunikacji między niemodalnym arkuszem właściwości a obiektem zewnętrznym, do którego mają zastosowanie ustawienia właściwości. Ta implementacja jest znacznie łatwiejsza, jeśli pochodna jest Klasa z [CPropertySheet](reference/cpropertysheet-class.md) dla niemodalnego arkusza właściwości. W tym artykule przyjęto założenie, że zostało to zrobione.

Jedna metoda komunikacji między niemodalnym arkuszem właściwości a obiektem zewnętrznym (na przykład bieżący wybór w widoku) polega na zdefiniowaniu wskaźnika z arkusza właściwości do obiektu zewnętrznego. Zdefiniuj funkcję (o nazwie podobnej do `SetMyExternalObject` ) w `CPropertySheet` klasie pochodnej, aby zmienić wskaźnik zawsze, gdy fokus zmieni się z jednego obiektu zewnętrznego na inny. `SetMyExternalObject`Funkcja musi zresetować ustawienia dla każdej strony właściwości, aby odzwierciedlić nowo wybrany obiekt zewnętrzny. Aby to osiągnąć, `SetMyExternalObject` Funkcja musi być w stanie uzyskać dostęp do obiektów [CPropertyPage](reference/cpropertypage-class.md) należących do `CPropertySheet` klasy.

Najbardziej wygodnym sposobem zapewnienia dostępu do stron właściwości w arkuszu właściwości jest osadzenie `CPropertyPage` obiektów w `CPropertySheet` obiekcie pochodnym. Osadzenie `CPropertyPage` obiektów w `CPropertySheet` obiekcie pochodnym różni się od typowego projektu modalnych okien dialogowych, gdzie właściciel arkusza właściwości tworzy `CPropertyPage` obiekty i przekazuje je do arkusza właściwości za pośrednictwem [CPropertySheet:: AddPage](reference/cpropertysheet-class.md#addpage).

Istnieje wiele alternatywnych interfejsów użytkownika do określania, kiedy ustawienia niemodalnego arkusza właściwości mają być stosowane do obiektu zewnętrznego. Alternatywą jest zastosowanie ustawień bieżącej strony właściwości zawsze wtedy, gdy użytkownik zmieni dowolną wartość. Kolejną alternatywą jest udostępnienie przycisku Zastosuj, który umożliwia użytkownikowi gromadzenie zmian na stronach właściwości przed przekazaniem ich do obiektu zewnętrznego. Aby uzyskać informacje na temat sposobów obsługi przycisku Zastosuj, zobacz artykuł [obsługa przycisku Zastosuj](handling-the-apply-button.md).

## <a name="see-also"></a>Zobacz też

[Arkusze właściwości](property-sheets-mfc.md)<br/>
[Wymiana danych](exchanging-data.md)<br/>
[Praca z oknami dialogowymi w MFC](life-cycle-of-a-dialog-box.md)
