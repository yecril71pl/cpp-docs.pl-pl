---
title: Usuwanie wszystkich obiektów z kolekcji CObject | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], deleting in collections
- objects in CObject collections, deleting
- CObject class [MFC], deleting in collection
- collection classes [MFC], deleting all objects
- CObject class collection
- objects in CObject collections
- collection classes [MFC], shared objects
ms.assetid: 81d2c1d5-a0a5-46e1-8ab9-82b45cf7afd2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4f57e503e43bdb637b85e4642349203b9f2e8aa6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348826"
---
# <a name="deleting-all-objects-in-a-cobject-collection"></a>Usuwanie wszystkich obiektów z kolekcji CObject
W tym artykule opisano sposób usuwania wszystkich obiektów z kolekcji (bez usuwania samego obiektu kolekcji).  
  
 Aby usunąć wszystkie obiekty w kolekcji `CObject`s (lub obiektów pochodzących od `CObject`), używany jest jeden z techniki iteracji opisaną w artykule [podczas uzyskiwania dostępu do wszystkich elementów członkowskich kolekcji](../mfc/accessing-all-members-of-a-collection.md) można usunąć każdego obiektu w Włącz.  
  
> [!CAUTION]
>  Obiekty w kolekcjach może być udostępniane. Oznacza to kolekcji zachowuje wskaźnik do obiektu, ale inne części program może być również wskaźniki do tego samego obiektu. Należy zachować ostrożność, nie można usunąć obiektu, który jest współużytkowany, dopóki wszystkie części zostało ukończone, przy użyciu obiektu.  
  
 W tym artykule przedstawiono sposób usuwania obiektów:  
  
-   [Lista](#_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject)  
  
-   [Tablica](#_core_to_delete_all_elements_in_an_array)  
  
-   [Mapy](#_core_to_delete_all_elements_in_a_map)  
  
#### <a name="_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject"></a>  Aby usunąć wszystkie obiekty w postaci listy wskaźniki do CObject  
  
1.  Użyj `GetHeadPosition` i `GetNext` do iterację na liście.  
  
2.  Użyj **usunąć** operatora, aby usunąć każdego obiektu, ponieważ jest podczas iteracji.  
  
3.  Wywołanie `RemoveAll` funkcji, aby usunąć wszystkie elementy z listy, po usunięciu obiekty skojarzone z tymi elementami.  
  
 Poniższy przykład przedstawia sposób Usuń wszystkie obiekty z listy `CPerson` obiektów. Każdy obiekt na liście jest wskaźnik do `CPerson` obiekt, który pierwotnie został przydzielony na stosie.  
  
 [!code-cpp[NVC_MFCCollections#17](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_1.cpp)]  
  
 Ostatnim wywołaniu funkcji `RemoveAll`, jest funkcją członkowską listę, która usuwa wszystkie elementy z listy. Funkcja członkowska `RemoveAt` Usuwa pojedynczy element.  
  
 Zwróć uwagę, różnica między usunięcie elementu obiektu i usuwanie samego elementu. Usunięcie elementu z listy jedynie usuwa listy odwołania do obiektu. Obiekt nadal istnieje w pamięci. Po usunięciu obiektu przestaje istnieje i jest odzyskać jego pamięci. W związku z tym jest ważne usunąć element natychmiast po elementu obiekt został usunięty, dzięki czemu listy nie spróbuj uzyskać dostęp do obiektów, które już istnieją.  
  
#### <a name="_core_to_delete_all_elements_in_an_array"></a>  Aby usunąć wszystkie elementy tablicy  
  
1.  Użyj `GetSize` i liczby całkowitej wartości indeksów do iteracji tablicy.  
  
2.  Użyj **usunąć** operatora, aby usunąć każdego elementu, ponieważ jest podczas iteracji.  
  
3.  Wywołanie `RemoveAll` funkcji, aby usunąć wszystkie elementy z tablicy, po ich usunięciu.  
  
     Kod do usuwania wszystkich elementów tablicy jest następujący:  
  
     [!code-cpp[NVC_MFCCollections#18](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_2.cpp)]  
  
 Zgodnie z powyższym przykładzie listy można wywołać `RemoveAll` do usunięcia wszystkich elementów w tablicy lub `RemoveAt` można usunąć pojedynczego elementu.  
  
#### <a name="_core_to_delete_all_elements_in_a_map"></a> Aby usunąć wszystkie elementy na mapie  
  
1.  Użyj `GetStartPosition` i `GetNextAssoc` do iteracji tablicy.  
  
2.  Użyj **usunąć** operatora, aby usunąć klucza i/lub wartość dla każdego elementu mapy, ponieważ jest podczas iteracji.  
  
3.  Wywołanie `RemoveAll` funkcji, aby usunąć wszystkie elementy z mapy po ich usunięciu.  
  
     Kod do usuwania wszystkich elementów `CMap` kolekcja ma następującą składnię. Każdy element na mapie zawiera ciąg jako klucz i `CPerson` obiektu (pochodną `CObject`) jako wartość.  
  
     [!code-cpp[NVC_MFCCollections#19](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_3.cpp)]  
  
 Możesz wywołać `RemoveAll` Aby usunąć wszystkie elementy na mapie lub `RemoveKey` usunąć pojedynczy element z określonym kluczem.  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do wszystkich składowych kolekcji](../mfc/accessing-all-members-of-a-collection.md)

