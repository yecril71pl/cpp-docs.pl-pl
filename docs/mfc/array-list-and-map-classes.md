---
title: Klasy tablic, list i map
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [MFC], classes
- list classes [MFC]
- collection classes [MFC], maps
- map classes [MFC]
- collection classes [MFC], lists
ms.assetid: 81a13a7f-0c2c-4efd-b6bb-b4e624a0743d
ms.openlocfilehash: 9583d8263901c4a135a3ba1f560856b2a8915168
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626106"
---
# <a name="array-list-and-map-classes"></a>Klasy tablic, list i map

W celu obsługi agregacji danych Biblioteka klas udostępnia grupę klas kolekcji — tablic, list i map — które mogą przechowywać wiele obiektów i wstępnie zdefiniowane typy. Kolekcje są dynamicznie skalowane. Te klasy mogą być używane w dowolnym programie, niezależnie od tego, czy są przeznaczone dla systemu Windows, czy nie. Jednak są one najbardziej przydatne do implementowania struktur danych, które definiują klasy dokumentów w strukturze aplikacji. Można z nich łatwo tworzyć wyspecjalizowane klasy kolekcji lub można je utworzyć na podstawie klas szablonów. Aby uzyskać więcej informacji na temat tych metod, zobacz [kolekcje](collections.md)artykułów. Listę klas kolekcji szablonów można znaleźć w temacie [klasy szablonów dla tablic, list i map](template-classes-for-arrays-lists-and-maps.md).

Tablice są jednowymiarowymi strukturami danych, które są przechowywane w sposób ciągły w pamięci. Obsługują one bardzo szybki dostęp losowy, ponieważ adres pamięci dowolnego danego elementu można obliczyć, mnożąc indeks elementu o rozmiar elementu i dodając wynik do adresu podstawowego tablicy. Ale tablice są bardzo kosztowne, jeśli trzeba wstawić elementy do tablicy, ponieważ cała tablica poprzedzająca wstawiony element musi zostać przeniesiona, aby zwolnić miejsce dla elementu, który ma zostać wstawiony. W razie potrzeby tablice mogą się zwiększać i zmniejszać.

Listy są podobne do tablic, ale są przechowywane bardzo inaczej. Każdy element na liście zawiera również wskaźnik do poprzednich i następnych elementów, dzięki czemu jest to lista połączona podwójnie. Można bardzo szybko dodawać lub usuwać elementy, ponieważ takie działanie wymaga jedynie zmiany kilku wskaźników. Jednak przeszukiwanie listy może być kosztowne, ponieważ wszystkie wyszukiwania muszą zacząć działać na jednym z punktów końcowych listy.

Maps powiąże wartość klucza z wartością danych. Na przykład klucz mapy może być ciągiem i danymi wskaźnikiem do listy. Należy zażądać mapy, aby przekazać wskaźnik skojarzony z określonym ciągiem. Wyszukiwanie map jest szybkie, ponieważ usługi Maps używają tabel skrótów do wyszukiwania kluczy. Dodawanie i usuwanie elementów jest również szybkie. Mapy są często używane z innymi strukturami danych jako indeksami pomocniczymi. MFC używa specjalnego rodzaju mapy zwanej [mapą komunikatów](mapping-messages.md) do mapowania komunikatów systemu Windows na wskaźnik do funkcji obsługi dla tego komunikatu.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](class-library-overview.md)
