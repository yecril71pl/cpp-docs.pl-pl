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
ms.openlocfilehash: 2921fe4e4f10c96a096d30d8f842eecdfd644ca6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615908"
---
# <a name="deleting-all-objects-in-a-cobject-collection"></a>Usuwanie wszystkich obiektów z kolekcji CObject

W tym artykule wyjaśniono, jak usunąć wszystkie obiekty w kolekcji (bez usuwania samego obiektu kolekcji).

Aby usunąć wszystkie obiekty w kolekcji `CObject` s (lub obiektów uzyskanych z `CObject` ), należy użyć jednej z technik iteracji opisanych w artykule, aby [uzyskać dostęp do wszystkich elementów członkowskich kolekcji](accessing-all-members-of-a-collection.md) w celu usunięcia każdego z nich obiektów.

> [!CAUTION]
> Obiekty w kolekcjach mogą być udostępniane. Oznacza to, że kolekcja utrzymuje wskaźnik do obiektu, ale inne części programu mogą także mieć wskaźniki do tego samego obiektu. Należy zachować ostrożność, aby nie usuwać obiektu, który jest współużytkowany do momentu zakończenia wszystkich części przy użyciu obiektu.

W tym artykule opisano sposób usuwania obiektów w programie:

- [Lista](#_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject)

- [Tablica](#_core_to_delete_all_elements_in_an_array)

- [Mapa](#_core_to_delete_all_elements_in_a_map)

#### <a name="to-delete-all-objects-in-a-list-of-pointers-to-cobject"></a><a name="_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject"></a>Aby usunąć wszystkie obiekty z listy wskaźników do CObject

1. Użyj `GetHeadPosition` i, `GetNext` Aby wykonać iterację listy.

1. Użyj operatora **delete** , aby usunąć każdy obiekt w trakcie iteracji.

1. Wywołaj `RemoveAll` funkcję, aby usunąć wszystkie elementy z listy po usunięciu obiektów skojarzonych z tymi elementami.

Poniższy przykład pokazuje, jak usunąć wszystkie obiekty z listy `CPerson` obiektów. Każdy obiekt na liście jest wskaźnikiem do `CPerson` obiektu, który został pierwotnie przydzielony na stosie.

[!code-cpp[NVC_MFCCollections#17](codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_1.cpp)]

Ostatnim wywołaniem funkcji, `RemoveAll` , jest funkcja członkowska listy, która usuwa wszystkie elementy z listy. Funkcja członkowska `RemoveAt` usuwa pojedynczy element.

Zauważ różnicę między usunięciem obiektu elementu i usunięciem samego elementu. Usunięcie elementu z listy tylko usuwa odwołanie do tego obiektu. Obiekt nadal istnieje w pamięci. Po usunięciu obiektu przestaje istnieć i jego pamięć jest odzyskiwana. W związku z tym ważne jest, aby usunąć element natychmiast po usunięciu obiektu elementu, dzięki czemu lista nie będzie próbować uzyskać dostępu do obiektów, które już nie istnieją.

#### <a name="to-delete-all-elements-in-an-array"></a><a name="_core_to_delete_all_elements_in_an_array"></a>Aby usunąć wszystkie elementy w tablicy

1. Używaj `GetSize` i wartości indeksów całkowitych do iteracji w tablicy.

1. Użyj operatora **delete** , aby usunąć każdy element w trakcie iteracji.

1. Wywołaj `RemoveAll` funkcję, aby usunąć wszystkie elementy z tablicy po ich usunięciu.

   Kod służący do usuwania wszystkich elementów tablicy jest następujący:

   [!code-cpp[NVC_MFCCollections#18](codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_2.cpp)]

Podobnie jak w przypadku powyższego przykładu listy, można wywołać, `RemoveAll` Aby usunąć wszystkie elementy w tablicy lub `RemoveAt` usunąć pojedynczy element.

#### <a name="to-delete-all-elements-in-a-map"></a><a name="_core_to_delete_all_elements_in_a_map"></a>Aby usunąć wszystkie elementy na mapie

1. Używaj `GetStartPosition` i `GetNextAssoc` do iteracji w tablicy.

1. Użyj operatora **delete** , aby usunąć klucz i/lub wartość dla każdego elementu mapy w miarę napotkania w iteracji.

1. Wywołaj `RemoveAll` funkcję, aby usunąć wszystkie elementy z mapy po ich usunięciu.

   Kod służący do usuwania wszystkich elementów `CMap` kolekcji jest następujący. Każdy element w mapie ma ciąg jako klucz i `CPerson` obiekt (pochodny od `CObject` ) jako wartość.

   [!code-cpp[NVC_MFCCollections#19](codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_3.cpp)]

Można wywołać, `RemoveAll` Aby usunąć wszystkie elementy na mapie lub `RemoveKey` usunąć pojedynczy element z określonym kluczem.

## <a name="see-also"></a>Zobacz też

[Uzyskiwanie dostępu do wszystkich elementów członkowskich kolekcji](accessing-all-members-of-a-collection.md)
