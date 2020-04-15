---
title: Usuwanie wszystkich obiektów z kolekcji CObject
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], deleting in collections
- objects in CObject collections, deleting
- CObject class [MFC], deleting in collection
- collection classes [MFC], deleting all objects
- CObject class collection
- objects in CObject collections
- collection classes [MFC], shared objects
ms.assetid: 81d2c1d5-a0a5-46e1-8ab9-82b45cf7afd2
ms.openlocfilehash: 303b8a566a730c5abd06d51fb7977174e19a6435
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370540"
---
# <a name="deleting-all-objects-in-a-cobject-collection"></a>Usuwanie wszystkich obiektów z kolekcji CObject

W tym artykule wyjaśniono, jak usunąć wszystkie obiekty w kolekcji (bez usuwania samego obiektu kolekcji).

Aby usunąć wszystkie obiekty w `CObject`kolekcji s (lub `CObject`obiektów pochodzących z ), należy użyć jednej z technik iteracji opisanych w artykule [Dostęp do wszystkich członków kolekcji,](../mfc/accessing-all-members-of-a-collection.md) aby usunąć każdy obiekt po kolei.

> [!CAUTION]
> Obiekty w kolekcjach mogą być współużytkowane. Oznacza to, że kolekcja przechowuje wskaźnik do obiektu, ale inne części programu może również mieć wskaźniki do tego samego obiektu. Należy uważać, aby nie usunąć obiektu, który jest współużytkowane, dopóki wszystkie części nie zostaną zakończone przy użyciu obiektu.

W tym artykule pokazano, jak usunąć obiekty w:

- [Lista](#_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject)

- [Tablicy](#_core_to_delete_all_elements_in_an_array)

- [Mapa](#_core_to_delete_all_elements_in_a_map)

#### <a name="to-delete-all-objects-in-a-list-of-pointers-to-cobject"></a><a name="_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject"></a>Aby usunąć wszystkie obiekty z listy wskaźników do CObject

1. Użyj `GetHeadPosition` `GetNext` i iterować przez listę.

1. Operator **usuwania** służy do usuwania każdego obiektu w miarę jego napotkania w iteracji.

1. Wywołanie `RemoveAll` funkcji, aby usunąć wszystkie elementy z listy po obiekty skojarzone z tymi elementami zostały usunięte.

W poniższym przykładzie pokazano, jak `CPerson` usunąć wszystkie obiekty z listy obiektów. Każdy obiekt na liście jest `CPerson` wskaźnikiem do obiektu, który został pierwotnie przydzielony na stercie.

[!code-cpp[NVC_MFCCollections#17](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_1.cpp)]

Ostatnie wywołanie `RemoveAll`funkcji , jest funkcją elementu członkowskiego listy, która usuwa wszystkie elementy z listy. Funkcja `RemoveAt` elementu członkowskiego usuwa pojedynczy element.

Zwróć uwagę na różnicę między usunięciem obiektu elementu a usunięciem samego elementu. Usunięcie elementu z listy jedynie usuwa odwołanie listy do obiektu. Obiekt nadal istnieje w pamięci. Po usunięciu obiektu przestaje istnieć, a jego pamięć zostanie odzyskana. W związku z tym ważne jest, aby usunąć element natychmiast po obiekt elementu został usunięty, tak aby lista nie będzie próbować uzyskać dostęp do obiektów, które już nie istnieją.

#### <a name="to-delete-all-elements-in-an-array"></a><a name="_core_to_delete_all_elements_in_an_array"></a>Aby usunąć wszystkie elementy w tablicy

1. Użyj `GetSize` i wartości indeksu liczby całkowitej, aby iterować za pośrednictwem tablicy.

1. Użyj **delete** operator, aby usunąć każdy element, jak to napotkane w iteracji.

1. Wywołanie `RemoveAll` funkcji, aby usunąć wszystkie elementy z tablicy po ich usunięciu.

   Kod do usuwania wszystkich elementów tablicy jest następujący:

   [!code-cpp[NVC_MFCCollections#18](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_2.cpp)]

Podobnie jak w przykładzie listy `RemoveAll` powyżej, można wywołać, aby usunąć wszystkie elementy w tablicy lub `RemoveAt` usunąć pojedynczy element.

#### <a name="to-delete-all-elements-in-a-map"></a><a name="_core_to_delete_all_elements_in_a_map"></a>Aby usunąć wszystkie elementy na mapie

1. Użyj `GetStartPosition` `GetNextAssoc` i iterować za pośrednictwem tablicy.

1. Użyj **delete** operator, aby usunąć klucz i/lub wartość dla każdego elementu mapy, jak to napotkane w iteracji.

1. Wywołanie `RemoveAll` funkcji, aby usunąć wszystkie elementy z mapy po ich usunięciu.

   Kod do usuwania wszystkich elementów `CMap` kolekcji jest w następujący sposób. Każdy element na mapie ma ciąg jako `CPerson` klucz i `CObject`obiekt (pochodną ) jako wartość.

   [!code-cpp[NVC_MFCCollections#19](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_3.cpp)]

Można wywołać, `RemoveAll` aby usunąć wszystkie `RemoveKey` elementy na mapie lub usunąć pojedynczy element z określonym kluczem.

## <a name="see-also"></a>Zobacz też

[Uzyskiwanie dostępu do wszystkich elementów członkowskich kolekcji](../mfc/accessing-all-members-of-a-collection.md)
