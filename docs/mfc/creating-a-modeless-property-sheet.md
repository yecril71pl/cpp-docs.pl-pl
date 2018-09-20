---
title: Tworzenie niemodalnego arkusza właściwości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modeless property sheets
- property sheets, modeless
- Create method [MFC], property sheets
ms.assetid: eafd8a92-cc67-4a69-a5fb-742c920d1ae8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 16b0a558dcae7d2bf35cf530abfea15ef6f8138a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378101"
---
# <a name="creating-a-modeless-property-sheet"></a>Tworzenie niemodalnego arkusza właściwości

Zwykle będzie modalne arkuszy właściwości, które można utworzyć. Używając modalny arkusz właściwości użytkownika należy zamknąć arkusza właściwości, przed rozpoczęciem korzystania z innych części aplikacji. W tym artykule opisano metody, które umożliwia tworzenie niemodalnego arkusza właściwości, która umożliwia użytkownikowi nie zamykaj arkusza właściwości podczas korzystania z innych części aplikacji.

Aby wyświetlić arkusz właściwości jako niemodalnego okna dialogowego zamiast jako modalne okno dialogowe, należy wywołać [CPropertySheet::Create](../mfc/reference/cpropertysheet-class.md#create) zamiast [DoModal](../mfc/reference/cpropertysheet-class.md#domodal). Należy także zaimplementować kilka dodatkowych zadań, aby obsługiwać niemodalnego arkusza właściwości.

Jedną z dodatkowych zadań jest wymiana danych między arkusza właściwości i zewnętrznego obiektu, który modyfikuje po otwarciu arkusza właściwości. Zwykle jest to samo zadanie, jak w przypadku standardowych Niemodalne okna dialogowe. Część tego zadania jest zaimplementowanie kanał komunikacji między niemodalnego arkusza właściwości i obiekcie zewnętrznym, do którego odnoszą się ustawienia właściwości. Ta implementacja jest znacznie łatwiejsze, jeśli wyprowadzić klasę z [CPropertySheet](../mfc/reference/cpropertysheet-class.md) dla Twojego niemodalnego arkusza właściwości. W tym artykule przyjęto założenie, że zostało to zrobione.

Jedną z metod komunikacji między niemodalnego arkusza właściwości i zewnętrznych obiektów (bieżące zaznaczenie w widoku, na przykład) polega na zdefiniowaniu wskaźnika z arkusza właściwości do obiektu zewnętrznego. Zdefiniuj funkcję (o nazwie podobny `SetMyExternalObject`) w `CPropertySheet`-klasy, aby zmienić wskaźnik zawsze wtedy, gdy fokus zmieni się z jednego obiektu zewnętrznego do innego. `SetMyExternalObject` Funkcja wymaga zresetowanie ustawień dla każdej strony właściwości w celu uwzględnienia nowo wybranego obiektu zewnętrznego. Aby to osiągnąć, `SetMyExternalObject` funkcja musi być w stanie uzyskać dostęp do [CPropertyPage](../mfc/reference/cpropertypage-class.md) obiektów należących do `CPropertySheet` klasy.

Najwygodniejszym sposobem zapewnienia dostępu do strony właściwości w arkuszu właściwości jest osadzenie `CPropertyPage` obiekty w `CPropertySheet`-pochodnych obiektu. Osadzanie `CPropertyPage` obiekty w `CPropertySheet`-obiektu pochodnej różni się od typowego projekt modalnych okien dialogowych, gdy właściciel tego arkusza właściwości tworzy `CPropertyPage` obiektów i przekazuje je do arkusza właściwości, za pośrednictwem [ CPropertySheet::AddPage](../mfc/reference/cpropertysheet-class.md#addpage).

Istnieje wiele alternatyw interfejsu użytkownika, określania stosowania ustawień niemodalnego arkusza właściwości do obiektu zewnętrznego. Jeden alternatywa to mają zostać zastosowane ustawienia bieżącej strony właściwości, zawsze wtedy, gdy użytkownik zmieni się dowolna wartość. Innym sposobem jest zapewnienie przycisk Zastosuj, który umożliwia użytkownikowi accumulate zmiany na stronach właściwości przed zatwierdzeniem je do obiektu zewnętrznego. Aby uzyskać informacje dotyczące sposobów, aby obsłużyć przycisk Zastosuj, zobacz artykuł [Obsługa przycisku Zastosuj](../mfc/handling-the-apply-button.md).

## <a name="see-also"></a>Zobacz też

[Arkusze właściwości](../mfc/property-sheets-mfc.md)<br/>
[Wymiana danych](../mfc/exchanging-data.md)<br/>
[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

