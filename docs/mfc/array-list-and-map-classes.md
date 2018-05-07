---
title: Array, listy i mapowania klas | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- arrays [MFC], classes
- list classes [MFC]
- collection classes [MFC], maps
- map classes [MFC]
- collection classes [MFC], lists
ms.assetid: 81a13a7f-0c2c-4efd-b6bb-b4e624a0743d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41dfe0b36548d87b5e0501c557e70f3cf11eea5d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="array-list-and-map-classes"></a>Klasy tablic, list i map
Obsługa wartości zagregowanych danych, biblioteki klas zawiera grupę klasy kolekcji — stałych, list i map — które mogą zawierać wiele obiektów i wstępnie zdefiniowanych typów. Kolekcje są dynamicznie o rozmiarze. Te klasy mogą być używane w programach, czy napisane dla systemu Windows, czy nie. Są one jednak najbardziej przydatny w przypadku implementowania struktury danych, które zdefiniowanie klas dokumentów w ramach aplikacji. Klasy specjalne kolekcji można łatwo pochodzi z tych lub można utworzyć je w oparciu klasy szablonu. Aby uzyskać więcej informacji o tych metod, zobacz artykuł [kolekcji](../mfc/collections.md). Lista szablonu klasy kolekcji, zobacz artykuł [klasy szablonów dla tablic, list i map](../mfc/template-classes-for-arrays-lists-and-maps.md).  
  
 Tablice są struktury jednowymiarowa danych, które są połączone ze sobą przechowywane w pamięci. Obsługują one dostęp do bardzo szybkiego losowego, ponieważ adres pamięci żadnych danego elementu, może zostać obliczona przez pomnożenie indeks elementu według rozmiaru elementu i dodanie wynik do adres podstawowy tablicy. Ale są bardzo kosztowna, jeśli masz wstawianie elementów do tablicy, od ostatnich tablicy cały element dodaje ma do przeniesienia, aby zwolnić miejsce dla elementu, który ma zostać wstawiony tablic. Tablice można zwiększyć lub zmniejszyć w razie potrzeby.  
  
 Listy są podobne do tablic, ale są przechowywane w bardzo inaczej. Każdy element na liście także wskaźnik do poprzedniego i następnego elementów, dzięki czemu podwójnie połączonej listy. Jest bardzo szybko, aby dodać lub usunąć elementy, ponieważ dzięki temu tylko obejmuje zmiana kilka wskazówek. Jednak wyszukiwanie listy może być kosztowne, ponieważ wszystkie wyszukiwania konieczne uruchomienie na jeden z końców listy.  
  
 Mapy odnoszą się wartość klucza do wartości danych. Na przykład klucz mapy może być ciąg i danych wskaźnik do listy. Czy poproś mapy daje wskaźnika skojarzonego z konkretnym ciągiem. Mapa wyszukiwań są szybkie, ponieważ mapy Użyj skrótu tabel odnośników klucza. Dodawanie i usuwanie elementów jest również szybkie. Mapy często są używane przez inne struktury danych jako indeksów pomocniczych. MFC używa specjalny rodzaj mapy o nazwie [mapy komunikatów](../mfc/mapping-messages.md) mapowania komunikaty systemu Windows na wskaźnik do funkcji obsługi dla tej wiadomości.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

