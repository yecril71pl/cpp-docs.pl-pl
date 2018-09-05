---
title: Klasy kolekcji ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DestructElements function
- collection classes, choosing
- ConstructElements function
- SerializeElements function
- traits classes
- collection classes, about collection classes
- CTraits classes
- collection classes
ms.assetid: 4d619d46-5b4e-41dd-b9fd-e86b1fbc00b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c40303e0353e9f7ef3740e55381306507878b72b
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752635"
---
# <a name="atl-collection-classes"></a>Klasy kolekcji ATL

ATL zawiera wiele klas do przechowywania i uzyskiwania dostępu do danych. Klasy, które użytkownik zdecyduje się użyć zależy od kilku czynników, takich jak:

- Ilość danych, które mają być przechowywane

- Wydajność w porównaniu z wydajnością podczas uzyskiwania dostępu do danych

- Możliwość dostępu do danych za pomocą indeksu lub klucza

- Jak dane są porządkowane

- Osobistych preferencji

## <a name="small-collection-classes"></a>Klasy kolekcji małe

ATL zawiera następujące klasy tablic radzenia sobie z małej liczby obiektów. Te klasy są jednak ograniczone i przeznaczone do użytku wewnętrznego przez ATL. Nie zaleca się używania ich w swoich programach.

|Class|Typ magazynu danych|
|-----------|--------------------------|
|[CSimpleArray](../atl/reference/csimplearray-class.md)|Implementuje klasę tablicy radzenia sobie z małej liczby obiektów.|
|[CSimpleMap](../atl/reference/csimplemap-class.md)|Implementuje klasę mapowania radzenia sobie z małej liczby obiektów.|

## <a name="general-purpose-collection-classes"></a>Klasy kolekcji ogólnego przeznaczenia

Klasy postępuj zgodnie z implementacji tablic, list i map i są dostępne jako klasy kolekcji ogólnego przeznaczenia:

|Class|Typ magazynu danych|
|-----------|--------------------------|
|[CAtlArray](../atl/reference/catlarray-class.md)|Implementuje tablicy.|
|[CAtlList](../atl/reference/catllist-class.md)|Implementuje listę.|
|[CAtlMap](../atl/reference/catlmap-class.md)|Implementuje struktury mapowania, według których dane mogą odwoływać się do klucza lub wartości.|
|[CRBMap](../atl/reference/crbmap-class.md)|Implementuje struktury mapowania przy użyciu algorytmu Red czarny.|
|[CRBMultiMap](../atl/reference/crbmultimap-class.md)|Implementuje strukturę multimapping Red czarny.|

W ramach tych zajęć wyłapuje wiele błędy programowania, gdy są używane w kompilacjach debugowania, ale pokazano wydajność, te testy nie zostaną wykonane w sprzedaży detalicznej.

## <a name="specialized-collection-classes"></a>Klasy kolekcji specjalne

Dostępne są również bardziej wyspecjalizowane klasy kolekcji do zarządzania i wskaźnikami interfejsu pamięci:

|Class|Cel|
|-----------|-------------|
|[CAutoPtrArray](../atl/reference/cautoptrarray-class.md)|Udostępnia metody przydatne przy konstruowaniu tablicy inteligentnych wskaźników.|
|[CAutoPtrList](../atl/reference/cautoptrlist-class.md)|Udostępnia metody przydatne podczas tworzenia listy inteligentne wskaźniki.|
|[CComUnkArray](../atl/reference/ccomunkarray-class.md)|Magazyny `IUnknown` wskaźników i jest przeznaczony do użycia jako parametr do [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) klasy szablonu.|
|[CHeapPtrList](../atl/reference/cheapptrlist-class.md)|Udostępnia metody przydatne podczas tworzenia listy wskaźników sterty.|
|[CInterfaceArray](../atl/reference/cinterfacearray-class.md)|Udostępnia metody przydatne przy konstruowaniu tablicy wskaźników interfejsu COM.|
|[CInterfaceList](../atl/reference/cinterfacelist-class.md)|Udostępnia metody przydatne podczas tworzenia listy wskaźniki interfejsu COM.|

## <a name="choosing-a-collection-class"></a>Wybieranie klasy kolekcji

Każdą z klas kolekcji dostępne oferuje różną charakterystykę wydajności, jak pokazano w poniższej tabeli.

- Kolumny, 2 i 3 opisano każdej klasy porządkowanie i dostęp do właściwości. W tabeli termin "uporządkowane" oznacza, że kolejność, w którym elementy są wstawiane i usuwane określa ich kolejność, w kolekcji; nie oznacza to, że elementy są sortowane według ich zawartości. Termin "indexed" oznacza, że elementy w kolekcji mogą być pobierane według indeksu liczba całkowita, podobnie jak elementy w tablicy typowy.

- Kolumny 4 i 5 opisują wydajność każdej klasy. W aplikacji, które wymagają wielu wstawień do kolekcji szybkości wstawiania może być szczególnie ważne; dla innych aplikacji szybkość wyszukiwania może być niezwykle ważne.

- Kolumna 6 opisuje, czy każdy kształt zezwala na zduplikowane elementy.

- Wydajność operacji klasy danej kolekcji jest wyrażona w relacji między czasem potrzebnym do ukończenia operacji i liczbę elementów w kolekcji. Operacja przełączania ilość czasu, która zwiększa liniowo jako liczba wzrasta elementów jest określana jako algorytm O(n). Z drugiej strony operacja trwa okres czasu, która zwiększa się mniej jako liczba wzrasta elementów jest opisana algorytmu O (log n). W związku z tym pod względem wydajności, algorytmów O (log n), której algorytmy O(n) coraz częściej jako liczba wzrasta elementów.

### <a name="collection-shape-features"></a>Kolekcja elementów kształtu

|Kształt|Uporządkowane|Indeksowane|Wstaw<br /><br /> — element|Wyszukaj<br /><br /> określony element|Zduplikowany<br /><br /> elementy|
|-----------|--------------|--------------|---------------------------|--------------------------------------|-----------------------------|
|Lista|Tak|Nie|Szybko (stały czas)|Powolne O(n)|Tak|
|Tablica|Tak|Przez int (stały czas)|Powolne O(n), z wyjątkiem sytuacji, w przypadku wstawiania na końcu, w których wielkość stałym czasie|Powolne O(n)|Tak|
|Mapy|Nie|Według klucza (stały czas)|Szybko (stały czas)|Szybko (stały czas)|Tak (wartości) (kluczy)|
|Mapa red czarny|Tak (według kluczy)|Według klucza O (log n)|Szybkie O (log n)|Szybkie O (log n)|Nie|
|Multimap red czarny|Tak (według kluczy)|Według klucza O(log n) (wiele wartości dla każdego klucza)|Szybkie O (log n)|Szybkie O (log n)|Tak (wiele wartości dla każdego klucza)|

## <a name="using-ctraits-objects"></a>Za pomocą ctraits — obiekty

Ponieważ klasy kolekcji ATL może służyć do przechowywania różnorodnych typy danych zdefiniowane przez użytkownika, może być przydatne można było przesłonić ważnych funkcji, takich jak porównania. Jest to osiągane przy użyciu ctraits — klasy.

Ctraits — klasy są podobne do, ale bardziej elastyczny niż funkcji pomocnika klasy kolekcji MFC; zobacz [pomocnicy klasy kolekcji](../mfc/reference/collection-class-helpers.md) Aby uzyskać więcej informacji.

Podczas tworzenia klasy kolekcji, istnieje możliwość określenia ctraits — klasy. Ta klasa zawiera kod, który będzie wykonywać operacje takie jak porównania, gdy wywoływana za pomocą innych metod, które tworzą klasy kolekcji. Na przykład obiekt listy zawiera własnych struktur zdefiniowanych przez użytkownika, można ponownie zdefiniować testu równości, aby porównać tylko niektórych zmiennych Członkowskich. W ten sposób obiekt listy Znajdź metoda będzie działać w sposób bardziej użyteczne.

## <a name="example"></a>Przykład

### <a name="code"></a>Kod

[!code-cpp[NVC_ATL_Utilities#112](../atl/codesnippet/cpp/atl-collection-classes_1.cpp)]

## <a name="comments"></a>Komentarze

Aby uzyskać listę ctraits — klasy, zobacz [klas kolekcji](../atl/collection-classes.md).

Poniższy diagram przedstawia hierarchii klas dla ctraits — klasy.

![Cechy hierarchii klas kolekcji](../atl/media/vctraitscollectionclasseshierarchy.gif "vctraitscollectionclasseshierarchy")

## <a name="collection-classes-samples"></a>Przykłady klasy kolekcji

Poniższe przykłady pokazują klas kolekcji:

- [Przykładowe MMXSwarm](../visual-cpp-samples.md)

- [Przykładowe DynamicConsumer](../visual-cpp-samples.md)

- [Przykładowe UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)

- [Przykładowe Neon](../visual-cpp-samples.md)

## <a name="see-also"></a>Zobacz też

[Pojęcia](../atl/active-template-library-atl-concepts.md)   
[Klasy kolekcji](../atl/collection-classes.md)

