---
title: Omówienie klasy kolekcji ATL
ms.date: 11/19/2018
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
ms.openlocfilehash: 039af388a3713540c6ba7d39e8b639cf83d291ff
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040863"
---
# <a name="atl-collection-classes"></a>Klasy kolekcji ATL

ATL udostępnia wiele klas do przechowywania i uzyskiwania dostępu do danych. Klasa, która ma być używana, zależy od kilku czynników, w tym:

- Ilość danych, które mają być przechowywane

- Wydajność i wydajność podczas uzyskiwania dostępu do danych

- Możliwość dostępu do danych za pomocą indeksu lub klucza

- Jak są uporządkowane dane

- Preferencja osobista

## <a name="small-collection-classes"></a>Małe klasy kolekcji

ATL oferuje następujące klasy macierzy do obsługi małych liczb obiektów. Jednak te klasy są ograniczone i przeznaczone do użytku wewnętrznego przez ATL. Nie zaleca się korzystania z nich w swoich programach.

|Klasa|Typ magazynu danych|
|-----------|--------------------------|
|[CSimpleArray](../atl/reference/csimplearray-class.md)|Implementuje klasę Array do celów związanych z małą liczbą obiektów.|
|[CSimpleMap](../atl/reference/csimplemap-class.md)|Implementuje klasę mapowania na potrzeby postępowania z niewielką liczbą obiektów.|

## <a name="general-purpose-collection-classes"></a>Klasy kolekcji Ogólnego przeznaczenia

Poniższe klasy implementują tablice, listy i mapy i są udostępniane jako klasy kolekcji ogólnego przeznaczenia:

|Klasa|Typ magazynu danych|
|-----------|--------------------------|
|[CAtlArray](../atl/reference/catlarray-class.md)|Implementuje tablicę.|
|[CAtlList](../atl/reference/catllist-class.md)|Implementuje listę.|
|[CAtlMap](../atl/reference/catlmap-class.md)|Implementuje strukturę mapowania, zgodnie z którym dane mogą być przywoływane przez klucz lub wartość.|
|[CRBMap](../atl/reference/crbmap-class.md)|Implementuje strukturę mapowania przy użyciu algorytmu Red-Black.|
|[CRBMultiMap](../atl/reference/crbmultimap-class.md)|Implementuje strukturę wielomap z czerwonym kolorem.|

Te klasy będą zalewkować wiele błędów programistycznych podczas korzystania z kompilacji debugowania, ale w celu zapewnienia wydajności te testy nie będą wykonywane w kompilacjach detalicznych.

## <a name="specialized-collection-classes"></a>Wyspecjalizowane klasy kolekcji

Bardziej wyspecjalizowane klasy kolekcji są również udostępniane do zarządzania wskaźnikami pamięci i wskaźnikami interfejsu:

|Klasa|Przeznaczenie|
|-----------|-------------|
|[CAutoPtrArray](../atl/reference/cautoptrarray-class.md)|Zapewnia metody przydatne podczas konstruowania tablicy inteligentnych wskaźników.|
|[CAutoPtrList](../atl/reference/cautoptrlist-class.md)|Zapewnia metody przydatne podczas konstruowania listy inteligentnych wskaźników.|
|[CComUnkArray](../atl/reference/ccomunkarray-class.md)|Przechowuje `IUnknown` wskaźniki i jest przeznaczony do użycia jako parametr klasy szablonu [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) .|
|[CHeapPtrList](../atl/reference/cheapptrlist-class.md)|Zapewnia metody przydatne podczas konstruowania listy wskaźników sterty.|
|[CInterfaceArray](../atl/reference/cinterfacearray-class.md)|Zapewnia metody przydatne podczas konstruowania tablicy wskaźników interfejsu COM.|
|[CInterfaceList](../atl/reference/cinterfacelist-class.md)|Zapewnia metody przydatne podczas konstruowania listy wskaźników interfejsu COM.|

## <a name="choosing-a-collection-class"></a>Wybieranie klasy kolekcji

Każda z dostępnych klas kolekcji oferuje różne charakterystyki wydajności, jak pokazano w poniższej tabeli.

- Kolumny 2 i 3 opisują właściwości określania kolejności i dostępu każdej klasy. W tabeli termin "uporządkowane" oznacza, że kolejność, w której elementy są wstawiane i usuwane, określa ich kolejność w kolekcji. nie oznacza to, że elementy są sortowane według ich zawartości. Termin "Indexed" oznacza, że elementy w kolekcji mogą być pobierane przez indeks liczby całkowitej, podobnie jak elementy w typowej tablicy.

- Kolumny 4 i 5 opisują wydajność każdej klasy. W aplikacjach, które wymagają wielu operacji wstawiania do kolekcji, szybkość wstawiania może być szczególnie ważna; w przypadku innych aplikacji szybkość wyszukiwania może być bardziej ważna.

- Kolumna 6 zawiera informacje o tym, czy każdy kształt umożliwia duplikowanie elementów.

- Wydajność danej operacji klasy kolekcji jest wyrażona w zakresie relacji między czasem wymaganym do ukończenia operacji i liczbą elementów w kolekcji. Operacja trwa przez czas, który zwiększa się liniowo w miarę wzrostu liczby elementów, jest opisana jako algorytm O (n). Z kolei, operacja trwa przez pewien czas, który zwiększa mniejszą i mniejszą liczbę elementów, jest opisana jako algorytm O (log n). W związku z tym, w zakresie wydajności, algorytmy O (log n) outperform O (n) algorytmy więcej i więcej w miarę zwiększania liczby elementów.

### <a name="collection-shape-features"></a>Funkcje kształtu kolekcji

|Kształt|Zamówione|Pełnotekstowych|Wstaw<br /><br />  — element|Wyszukaj<br /><br /> określony element|Duplikuj<br /><br /> elementy|
|-----------|--------------|--------------|---------------------------|--------------------------------------|-----------------------------|
|Lista|Tak|Nie|Fast (stały czas)|Wolne O (n)|Tak|
|Tablica|Tak|Według int (stały czas)|Wolno O (n), chyba że wstawiasz na końcu, w którym przypadku stały czas|Wolne O (n)|Tak|
|Mapa|Nie|Według klucza (stały czas)|Fast (stały czas)|Fast (stały czas)|Nie (klucze) tak (wartości)|
|Mapa Red-Black|Tak (za pomocą klucza)|Według klucza O (log n)|Fast O (log n)|Fast O (log n)|Nie|
|Czerwony-czarny multimap|Tak (za pomocą klucza)|Według klucza O (log n) (wiele wartości na klucz)|Fast O (log n)|Fast O (log n)|Tak (wiele wartości na klucz)|

## <a name="using-ctraits-objects"></a>Korzystanie z obiektów CTraits

Jako że klasy kolekcji ATL mogą służyć do przechowywania szerokiego zakresu typów danych zdefiniowanych przez użytkownika, może być przydatne, aby przesłonić ważne funkcje, takie jak porównania. Jest to osiągane przy użyciu klas CTraits.

Klasy CTraits są podobne do, ale bardziej elastyczne niż, funkcje pomocnika klasy kolekcji MFC; Aby uzyskać więcej informacji, zobacz [Pomocnicy klasy kolekcji](../mfc/reference/collection-class-helpers.md) .

Podczas konstruowania klasy kolekcji można określić klasę CTraits. Ta klasa będzie zawierać kod, który wykona operacje, takie jak porównania, gdy są wywoływane przez inne metody, które tworzą klasę kolekcji. Na przykład jeśli obiekt listy zawiera własne struktury zdefiniowane przez użytkownika, możesz chcieć ponownie zdefiniować test równości, aby porównać tylko niektóre zmienne składowe. W ten sposób Metoda Find obiektu listy będzie działać w bardziej przydatny sposób.

## <a name="example"></a>Przykład

### <a name="code"></a>Kod

[!code-cpp[NVC_ATL_Utilities#112](../atl/codesnippet/cpp/atl-collection-classes_1.cpp)]

## <a name="comments"></a>Komentarze

Aby uzyskać listę klas CTraits, zobacz [klasy kolekcji](../atl/collection-classes.md).

Na poniższym diagramie przedstawiono hierarchię klas klas CTraits.

![Hierarchia cech dla klas kolekcji](../atl/media/vctraitscollectionclasseshierarchy.gif "Hierarchia cech dla klas kolekcji")

## <a name="collection-classes-samples"></a>Przykłady klas kolekcji

Następujące przykłady przedstawiają klasy kolekcji:

- [Przykład MMXSwarm](../overview/visual-cpp-samples.md)

- [Przykład DynamicConsumer](../overview/visual-cpp-samples.md)

- [Przykład UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)

- [Przykład neonu](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>Zobacz także

[Pojęcia](../atl/active-template-library-atl-concepts.md)<br/>
[Klasy kolekcji](../atl/collection-classes.md)
