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
ms.openlocfilehash: 95d4cec61b230df5a019655617a25b1dc309cde4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257972"
---
# <a name="deleting-all-objects-in-a-cobject-collection"></a>Usuwanie wszystkich obiektów z kolekcji CObject

W tym artykule wyjaśniono, jak można usunąć wszystkich obiektów z kolekcji (bez usuwania sam obiekt kolekcji).

Aby usunąć wszystkie obiekty w kolekcji `CObject`s (lub obiektów pochodzących od `CObject`), możesz użyć jednej z metod iteracji, opisaną w artykule [uzyskiwania dostępu do wszystkich elementów członkowskich kolekcji](../mfc/accessing-all-members-of-a-collection.md) można usunąć każdy obiekt w Włącz.

> [!CAUTION]
>  Mogą być udostępniane obiekty w kolekcjach. Oznacza to, że kolekcja przechowuje wskaźnik do obiektu, ale inne części programu, mogą także mieć wskaźniki do tego samego obiektu. Należy uważać, aby nie usunąć obiektu, który jest udostępniany, do momentu zakończenia wszystkich części za pomocą obiektu.

W tym artykule pokazano, jak usuwanie obiektów w programie:

- [Lista](#_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject)

- [Tablica](#_core_to_delete_all_elements_in_an_array)

- [Mapy](#_core_to_delete_all_elements_in_a_map)

#### <a name="_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject"></a>  Aby usunąć wszystkie obiekty w postaci listy wskaźników do obiektu CObject

1. Użyj `GetHeadPosition` i `GetNext` do iteracji przez listę.

1. Użyj **Usuń** operator można usunąć każdego obiektu, ponieważ jest podczas iteracji.

1. Wywołaj `RemoveAll` funkcję, aby usunąć wszystkie elementy z listy, po usunięciu obiektów skojarzonych z tymi elementami.

Poniższy przykład pokazuje, jak usunąć wszystkie obiekty z listy `CPerson` obiektów. Każdy obiekt na liście jest wskaźnikiem do `CPerson` obiekt, który pierwotnie został przydzielony na stosie.

[!code-cpp[NVC_MFCCollections#17](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_1.cpp)]

Ostatnie wywołanie funkcji `RemoveAll`, jest funkcją składową listy, która usuwa wszystkie elementy z listy. Funkcja elementu członkowskiego `RemoveAt` Usuwa pojedynczy element.

Zwróć uwagę na różnicę między usunięcie elementu obiektu i usuwanie samego elementu. Usuwanie elementu z listy jedynie usuwa listy odwołania do obiektu. Obiekt nadal znajduje się w pamięci. Po usunięciu obiektu przestaje istnieć i jego pamięci są odzyskiwane. W związku z tym należy usunąć element natychmiast, po elementu obiekt został usunięty, tak aby lista nie będzie podejmowana próba dostępu do obiektów, które już istnieją.

#### <a name="_core_to_delete_all_elements_in_an_array"></a>  Aby usunąć wszystkie elementy w tablicy

1. Użyj `GetSize` i liczby całkowitej wartości indeksu można wykonać iterację tablicy.

1. Użyj **Usuń** operator można usunąć każdego elementu, ponieważ jest podczas iteracji.

1. Wywołaj `RemoveAll` funkcję, aby usunąć wszystkie elementy z tablicy, po ich usunięciu.

   Kod do usuwania wszystkich elementów tablicy jest następująca:

   [!code-cpp[NVC_MFCCollections#18](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_2.cpp)]

Zgodnie z powyższym przykładzie listy może wywołać `RemoveAll` można usunąć wszystkich elementów w tablicy lub `RemoveAt` można usunąć pojedynczego elementu.

#### <a name="_core_to_delete_all_elements_in_a_map"></a> Aby usunąć wszystkich elementów w mapie.

1. Użyj `GetStartPosition` i `GetNextAssoc` można wykonać iterację tablicy.

1. Użyj **Usuń** operator można usunąć klucza i/lub wartość dla każdego elementu na mapie, ponieważ jest podczas iteracji.

1. Wywołaj `RemoveAll` funkcję, aby usunąć wszystkie elementy z mapy, po ich usunięciu.

   Usunięcie wszystkich elementów w kodzie `CMap` kolekcja jest w następujący sposób. Każdy element w mapie ma ciąg jako klucz i `CPerson` obiektu (pochodną `CObject`) jako wartość.

   [!code-cpp[NVC_MFCCollections#19](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_3.cpp)]

Możesz wywołać `RemoveAll` można usunąć wszystkich elementów w mapie lub `RemoveKey` można usunąć pojedynczego elementu z określonym kluczem.

## <a name="see-also"></a>Zobacz także

[Uzyskiwanie dostępu do wszystkich składowych kolekcji](../mfc/accessing-all-members-of-a-collection.md)
