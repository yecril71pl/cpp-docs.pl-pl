---
title: Klasy tablic, list i map
ms.date: 11/04/2016
f1_keywords:
- vc.classes.mfc
helpviewer_keywords:
- arrays [MFC], classes
- list classes [MFC]
- collection classes [MFC], maps
- map classes [MFC]
- collection classes [MFC], lists
ms.assetid: 81a13a7f-0c2c-4efd-b6bb-b4e624a0743d
ms.openlocfilehash: 0856a9de06d07b3851dc748644e84ba9c4b56c4f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601048"
---
# <a name="array-list-and-map-classes"></a>Klasy tablic, list i map

Obsługa wartości zagregowanych danych, biblioteka klas zawiera grupy klas kolekcji — tablic, list i map — który może zawierać wiele obiektów i wstępnie zdefiniowanych typów. Kolekcje są dynamicznie wielkości. Te klasy mogą być używane w dowolnym programie, czy napisane dla Windows, czy nie. Są najbardziej przydatne w przypadku implementowania struktur danych, które definiują swojej klasy dokumentów w ramach aplikacji. Można łatwo uzyskać klas wyspecjalizowanych kolekcji z tych lub możesz utworzyć je w oparciu o klasy szablonu. Aby uzyskać więcej informacji na temat tych metod, zobacz artykuł [kolekcje](../mfc/collections.md). Aby uzyskać listę klas kolekcji szablonów, zobacz artykuł [klasy szablonów dla tablic, list i map](../mfc/template-classes-for-arrays-lists-and-maps.md).

Tablice są struktur danych jednowymiarowej, które są przechowywane w sposób ciągły w pamięci. Obsługiwane są też bardzo szybko swobodnego dostępu, ponieważ adres pamięci dowolnego danego elementu mogą być obliczane przez pomnożenie indeks elementu przez rozmiar elementu i dodanie wyniku na adres bazowy tablicy. Ale tablice są bardzo kosztowna, jeśli użytkownik ma do wstawienia elementów do tablicy, od całej tablicy w ciągu ostatnich element wstawiony ma do przeniesienia w celu zwolnienia miejsca dla elementu, który ma zostać wstawiony. Tablice można zwiększyć lub zmniejszyć gdy jest to konieczne.

Listy są podobne do tablic, ale są przechowywane bardzo różny sposób. Każdy element na liście zawiera także wskaźnik do poprzedniego i następnego elementów, dzięki czemu podwójnie połączoną listą. Działa on bardzo szybko dodawać lub usuwać elementy, ponieważ to obejmuje tylko zmiana kilka wskazówek. Jednak wyszukiwania na liście może być kosztowne, ponieważ wszystkie wyszukiwania konieczne uruchomienie na jeden z końców listy.

Mapy odnoszą się wartość klucza do wartości danych. Na przykład klucz mapy może być ciąg i wskaźnik na listę danych. Czy poproś map umożliwiają kursor skojarzony z określonego ciągu. Map, wyszukiwania są szybkie, ponieważ mapy korzystanie z tabel skrótu klucza wyszukiwania. Dodawanie i usuwanie elementów jest również szybkie. Mapy są często używane z innych struktur danych jako indeksy pomocnicze. MFC używa specjalnego rodzaju mapy o nazwie [mapy komunikatów](../mfc/mapping-messages.md) do mapowania Windows wiadomości na wskaźnik do funkcji obsługi dla tego komunikatu.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)

