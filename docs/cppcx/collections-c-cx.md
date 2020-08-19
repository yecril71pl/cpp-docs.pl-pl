---
title: Kolekcje (C++/CX)
ms.date: 11/19/2018
ms.assetid: 914da30b-aac5-4cd7-9da3-a5ac08cdd72c
ms.openlocfilehash: 84c6ecad5ffb4920972faf5aa564103ec1f5b5df
ms.sourcegitcommit: 65fead53d56d531d71be42216056aca5f44def11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2020
ms.locfileid: "88610949"
---
# <a name="collections-ccx"></a>Kolekcje (C++/CX)

W programie C++/CX można korzystać z bezpłatnych kontenerów biblioteki szablonów standardowych (STL) lub dowolnego innego typu kolekcji zdefiniowanego przez użytkownika. Jednak w przypadku przekazywania kolekcji z powrotem i w środowisko wykonawcze systemu Windows ramach interfejsu ABI aplikacji, na przykład do kontrolki XAML lub do klienta JavaScript — należy użyć środowisko wykonawcze systemu Windows typów kolekcji.

Środowisko wykonawcze systemu Windows definiuje interfejsy dla kolekcji i powiązanych typów, a C++/CX zapewnia konkretne implementacje języka C++ w pliku nagłówkowym kolekcji. h. Na tej ilustracji przedstawiono relacje między typami kolekcji:

![Drzewo dziedziczenia języka C&#43;&#43;&#47;CX dla typów kolekcji](../cppcx/media/cppcxcollectionsinheritancetree.png "Drzewo dziedziczenia języka C&#43;&#43;&#47;CX dla typów kolekcji")

- [Klasa platform:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) jest podobna do [klasy std:: Vector](../standard-library/vector-class.md).

- Klasa [platform:: Collections:: map](../cppcx/platform-collections-map-class.md) jest podobna do [klasy std:: map](../standard-library/map-class.md).

- [Platform:: Collections:: VectorView Class](../cppcx/platform-collections-vectorview-class.md) i[platform:: Collections:: MapView, Klasa](../cppcx/platform-collections-mapview-class.md) jest tylko do odczytu wersji systemów `Vector` i `Map` .

- Iteratory są zdefiniowane w [przestrzeni nazw platform:: Collections](../cppcx/platform-collections-namespace.md). Te Iteratory spełniają wymagania dla iteratorów STL i umożliwiają użycie [std:: find](../standard-library/algorithm-functions.md#find),  [std:: count_if](../standard-library/algorithm-functions.md#count_if)i innych algorytmów STL w dowolnym [systemie Windows:: Foundation:: Collections](/uwp/api/windows.foundation.collections) Type lub [platform:: Collections](../cppcx/platform-collections-namespace.md) konkretny typ. Na przykład oznacza to, że można wykonać iterację kolekcji w składniku środowisko wykonawcze systemu Windows utworzonym w języku C# i zastosować do niego algorytm STL.

   > [!IMPORTANT]
   > Iteratory serwerów proxy `VectorIterator` i `VectorViewIterator` wykorzystują obiekty proxy `VectoryProxy<T>` oraz umożliwiają korzystanie `ArrowProxy<T>` z kontenerów STL. Aby uzyskać więcej informacji, zobacz "elementy VectorProxy" w dalszej części tego artykułu.

- Typy kolekcji C++/CX obsługują te same gwarancje bezpieczeństwa wątku, które obsługują kontenery STL.

- [Windows:: Foundation:: Collections:: IObservableVector](/uwp/api/windows.foundation.collections.iobservablevector-1) i [Windows:: Foundation:: Collections:: IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2) definiują zdarzenia, które są wywoływane, gdy kolekcja zostanie zmieniona na różne sposoby. Implementując te interfejsy,  [platform:: Collections:: map](../cppcx/platform-collections-map-class.md) i [platform:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) obsługuje powiązanie danych z kolekcjami XAML. Na przykład jeśli masz `Vector` dane, które są powiązane z danymi `Grid` , po dodaniu elementu do kolekcji, zmiana jest odzwierciedlana w interfejsie użytkownika siatki.

## <a name="vector-usage"></a>Użycie wektora

Gdy klasa musi przekazać kontener sekwencji do innego składnika środowisko wykonawcze systemu Windows, użyj funkcji [Windows:: Foundation:: Collections:: IVector \<T> ](/uwp/api/windows.foundation.collections.ivector-1) jako parametru lub typu zwracanego, a [platforma:: Collections:: Vector \<T> ](../cppcx/platform-collections-vector-class.md) jako konkretna implementacja. Jeśli spróbujesz użyć `Vector` typu w publicznej wartości zwracanej lub parametrze, zostanie zgłoszony błąd kompilatora C3986. Możesz naprawić ten błąd, zmieniając `Vector` element na `IVector` .

> [!IMPORTANT]
> Jeśli przekazujesz sekwencję w ramach własnego programu, użyj opcji lub, `Vector` `std::vector` ponieważ są one wydajniejsze niż `IVector` . Używaj `IVector` tylko w przypadku przekazywania kontenera między ABI.
>
> System typu środowisko wykonawcze systemu Windows nie obsługuje koncepcji tablic nieregularnych i w związku z tym nie można przekazać `IVector<Platform::Array<T>>` parametru jako wartości zwracanej lub metody. Aby przekazać nieregularną tablicę lub sekwencję sekwencji w ramach ABI, użyj `IVector<IVector<T>^>` .

`Vector<T>` dostarcza metody, które są wymagane do dodawania, usuwania i uzyskiwania dostępu do elementów w kolekcji, a także niejawnie konwertowane na `IVector<T>` . Można również użyć algorytmów STL w wystąpieniach `Vector<T>` . W poniższym przykładzie przedstawiono podstawowe użycie. Funkcja [BEGIN Function](../cppcx/begin-function.md) i [End](../cppcx/end-function.md) znajduje się w tym miejscu w `Platform::Collections` przestrzeni nazw, a nie w `std` przestrzeni nazw.

[!code-cpp[cx_collections#01](../cppcx/codesnippet/CPP/collections/class1.cpp#01)]

Jeśli masz istniejący kod, który używa `std::vector` i chcesz ponownie użyć go w składniku środowisko wykonawcze systemu Windows, po prostu Użyj jednego z `Vector` konstruktorów, które pobierają `std::vector` lub parę iteratorów do konstruowania w `Vector` punkcie, w którym kolekcja została przekazana przez ABI. Poniższy przykład pokazuje, jak używać `Vector` konstruktora przenoszenia do wydajnej inicjalizacji z `std::vector` . Po operacji przenoszenia oryginalna `vec` zmienna nie jest już prawidłowa.

[!code-cpp[cx_collections#02](../cppcx/codesnippet/CPP/collections/class1.cpp#02)]

Jeśli masz wektor ciągów, które muszą być przekazywane przez ABI w pewnym momencie w przyszłości, musisz zdecydować, czy należy utworzyć ciągi początkowo jako `std::wstring` typy, czy jako `Platform::String^` typy. Jeśli konieczne jest wykonanie wielu operacji przetwarzania ciągów, użyj `wstring` . W przeciwnym razie należy utworzyć ciągi jako `Platform::String^` typy i uniknąć kosztów ich późniejszego konwertowania. Należy również określić, czy te ciągi mają być umieszczane w, `std:vector` czy `Platform::Collections::Vector` wewnętrznie. Ogólnie rzecz biorąc, użyj, `std::vector` a następnie Utwórz `Platform::Vector` z niego tylko wtedy, gdy przekazujesz kontener przez ABI.

## <a name="value-types-in-vector"></a>Typy wartości w wektorze

Każdy element, który ma być przechowywany w [platformie:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) , musi obsługiwać porównanie równości (niejawnie lub przy użyciu niestandardowego [std:: equal_to](../standard-library/equal-to-struct.md) komparator. Wszystkie typy odwołań i wszystkie typy skalarne niejawnie obsługują porównania równości. Dla nieskalarnych typów wartości, takich jak [Windows:: Foundation::D atetime](/uwp/api/windows.foundation.datetime), lub na potrzeby niestandardowych porównań — na przykład `objA->UniqueID == objB->UniqueID` — należy podać obiekt funkcji niestandardowej.

## <a name="vectorproxy-elements"></a>Elementy VectorProxy

[Platform:: Collections:: VectorIterator](../cppcx/platform-collections-vectoriterator-class.md) i [platform:: Collections:: VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md) umożliwia użycie `range for` pętli i algorytmów, takich jak [std:: sort](../standard-library/algorithm-functions.md#sort) z kontenerem [IVector \<T> ](/uwp/api/windows.foundation.collections.ivector-1) . Ale do `IVector` elementów nie można uzyskać dostępu za poorednictwem dereferencji wskaźnika języka C++; dostęp do nich można uzyskać tylko za poorednictwem metod [GetAt](/uwp/api/windows.foundation.collections.ivector-1.getat) i [SetAt](/uwp/api/windows.foundation.collections.ivector-1.setat) . W związku z tym Iteratory używają klas proxy `Platform::Details::VectorProxy<T>` i `Platform::Details::ArrowProxy<T>` zapewniają dostęp do poszczególnych elementów za pomocą __\*__ operatorów, __->__ i __ \[ ]__ , zgodnie z wymaganiami biblioteki standardowej. Mówiąc `IVector<Person^> vec` , typ `*begin(vec)` to `VectorProxy<Person^>` . Jednak obiekt proxy jest prawie zawsze przezroczysty dla kodu. Te obiekty proxy nie są udokumentowane, ponieważ są przeznaczone tylko do użytku wewnętrznego przez Iteratory, ale warto wiedzieć, jak działa mechanizm.

Jeśli używasz `range for` pętli przez `IVector` kontenery, użyj, `auto&&` Aby włączyć zmienną iteratora w celu poprawnego powiązania do `VectorProxy` elementów. Jeśli używasz **`auto`** lub `auto&` , C4239 jest wywoływane Ostrzeżenie kompilatora i `VectoryProxy` jest ono wymienione w tekście ostrzegawczym.

Na poniższej ilustracji przedstawiono `range for` pętlę w `IVector<Person^>` . Zwróć uwagę, że wykonywanie zostało zatrzymane w punkcie przerwania w wierszu 64. Okno **QuickWatch** pokazuje, że zmienna iteratora `p` jest w rzeczywistości `VectorProxy<Person^>` , która ma `m_v` i `m_i` zmienne składowe. Jednak po wywołaniu `GetType` tej zmiennej zwraca identyczny typ do `Person` wystąpienia `p2` . Wnioskiem jest to, że chociaż `VectorProxy` i `ArrowProxy` mogą występować w **QuickWatch**, debuger niektórych błędów kompilatora lub inne miejsca, zazwyczaj nie trzeba jawnie kodu.

![VectorProxy w zakresie&#45;w oparciu o pętlę](../cppcx/media/vectorproxy-1.png "VectorProxy w zakresie&#45;w oparciu o pętlę")

Jeden scenariusz, w którym należy wykonać kod wokół obiektu serwera proxy, jest potrzebny do wykonania **`dynamic_cast`** na elementach — na przykład podczas wyszukiwania obiektów XAML określonego typu w `UIElement` kolekcji elementów. W takim przypadku należy najpierw rzutować element na [platformę:: Object](../cppcx/platform-object-class.md)^, a następnie wykonać dynamiczne rzutowanie:

```cpp
void FindButton(UIElementCollection^ col)
{
    // Use auto&& to avoid warning C4239
    for (auto&& elem : col)
    {
        Button^ temp = dynamic_cast<Button^>(static_cast<Object^>(elem));
        if (nullptr != temp)
        {
            // Use temp...
        }
    }
}
```

## <a name="map-usage"></a>Użycie mapy

Ten przykład pokazuje, jak wstawiać elementy i wyszukiwać je w [platformie:: Collections:: map](../cppcx/platform-collections-map-class.md), a następnie zwracać `Map` jako "tylko do odczytu [Windows:: Foundation:: Collections:: IMapView](/uwp/api/windows.foundation.collections.imapview-2) Type.

[!code-cpp[cx_collections#04](../cppcx/codesnippet/CPP/collections/class1.cpp#04)]

Ogólnie rzecz biorąc, w przypadku funkcji mapy wewnętrznej Preferuj `std::map` Typ z przyczyn związanych z wydajnością. Jeśli konieczne jest przekazanie kontenera między ABI, należy skonstruować [platformę:: Collections:: map](../cppcx/platform-collections-map-class.md) z elementu [std:: map](../standard-library/map-class.md) i zwrócić `Map` jako [Windows:: Foundation:: Collections:: IMAP](/uwp/api/windows.foundation.collections.imap-2). Jeśli spróbujesz użyć `Map` typu w publicznej wartości zwracanej lub parametrze, zostanie zgłoszony błąd kompilatora C3986. Możesz naprawić ten błąd, zmieniając `Map` element na `IMap` . W niektórych przypadkach — na przykład, jeśli nie tworzysz dużej liczby odnośników ani wstawień i przekazujesz kolekcję przez ABI często — może być tańsze `Platform::Collections::Map` od początku i uniknąć kosztu konwersji `std::map` . W każdym przypadku należy unikać wyszukiwania i wstawiania operacji, `IMap` ponieważ są one najmniej zgodne z trzema typami. Konwertuj na `IMap` tylko w punkcie, w którym przeszedł kontener w ABI.

## <a name="value-types-in-map"></a>Typy wartości w mapowaniu

Elementy w elemencie [platform:: Collections:: map](../cppcx/platform-collections-map-class.md) są uporządkowane. Każdy element, który ma być przechowywany w, `Map` musi obsługiwać mniej niż porównanie z ścisłym nieprawidłowym porządkowaniem, niejawnie lub przy użyciu niestandardowego [STL:: less](../standard-library/less-struct.md) komparator. Typy skalarne obsługują porównanie niejawnie. W przypadku typów wartości nieskalarnych, takich jak `Windows::Foundation::DateTime` lub niestandardowych porównań — na przykład `objA->UniqueID < objB->UniqueID` — należy podać niestandardowy komparator.

## <a name="collection-types"></a>Typy kolekcji

Kolekcje dzielą się na cztery kategorie: modyfikowalne wersje i wersje tylko do odczytu kolekcji sekwencji i kolekcji asocjacyjnych. Ponadto C++/CX rozszerza kolekcje, dostarczając trzy klasy iteratorów, które upraszczają dostęp do kolekcji.

Elementy kolekcji modyfikowalnej można zmienić, ale elementy kolekcji tylko do odczytu, która jest znana jako *Widok*, można odczytać tylko. Elementy klasy [platform:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) lub[platform:: Collections:: VectorView](../cppcx/platform-collections-vectorview-class.md) można uzyskać dostępu przy użyciu iteratora lub [wektora kolekcji:: GetAt](../cppcx/platform-collections-vector-class.md#getat) i indeksu. Do elementów kolekcji asocjacyjnej można uzyskać dostęp za pomocą [mapy kolekcji:: Lookup](../cppcx/platform-collections-map-class.md#lookup) i klucza.

[Platform:: Collections:: map, Klasa](../cppcx/platform-collections-map-class.md)<br/>
Modyfikowalna kolekcja asocjacyjna. Elementy mapy to pary klucz-wartość. Wyszukiwanie klucza w celu pobrania jego skojarzonej wartości i przechodzenia przez wszystkie pary klucz-wartość są obsługiwane.

`Map` i `MapView` są szablonem. w związku z tym można `<K, V, C = std::less<K>>` dostosować komparator.  Ponadto `Vector` i `VectorView` są szablonami w programie, `<T, E = std::equal_to<T>>` Aby można było dostosować zachowanie programu `IndexOf()` . Jest to ważne głównie dla `Vector` `VectorView` struktur wartości i. Na przykład, aby utworzyć wektor \<Windows::Foundation::DateTime> , należy podać niestandardowy komparator, ponieważ DateTime nie przeciąża operatora = =.

[Platform:: Collections:: MapView, Klasa](../cppcx/platform-collections-mapview-class.md)<br/>
Wersja programu `Map` .

[Platform:: Collections:: Vector, Klasa](../cppcx/platform-collections-vector-class.md)<br/>
Modyfikowalna kolekcja sekwencji. `Vector<T>` Program obsługuje dostęp losowy do czasu stałego oraz operacje [dołączania](../cppcx/platform-collections-vector-class.md#append) w czasie stałym.

[Platform:: Collections:: VectorView, Klasa](../cppcx/platform-collections-vectorview-class.md)<br/>
Wersja programu `Vector` .

[Platform:: Collections:: InputIterator, Klasa](../cppcx/platform-collections-inputiterator-class.md)<br/>
Iterator STL, który spełnia wymagania iteratora wejściowego STL.

[Platform:: Collections:: VectorIterator, Klasa](../cppcx/platform-collections-vectoriterator-class.md)<br/>
Iterator STL, który spełnia wymagania dla iteratora dostęp swobodny STL.

[Platform:: Collections:: VectorViewIterator, Klasa](../cppcx/platform-collections-vectorviewiterator-class.md)<br/>
Iterator STL, który spełnia wymagania  **`const`** iteratora dostępu swobodnego STL.

### <a name="begin-and-end-functions"></a>funkcje Begin () i End ()

Aby uprościć użycie STL do przetwarzania `Vector` ,,, `VectorView` `Map` `MapView` , i dowolnych `Windows::Foundation::Collections` obiektów, C++/CX obsługuje przeciążenia [funkcji BEGIN](../cppcx/begin-function.md) i [End funkcji](../cppcx/end-function.md) nienależących do elementu członkowskiego.

Poniższa tabela zawiera listę dostępnych iteratorów i funkcji.

|Iteratory|Funkcje|
|---------------|---------------|
|[Platform:: Collections:: VectorIterator\<T>](../cppcx/platform-collections-vectoriterator-class.md)<br /><br /> (Wewnętrznie przechowuje [system Windows:: Foundation:: Collections: \<T> : IVector](/uwp/api/windows.foundation.collections.ivector-1) i int.)|[Rozpocznij](../cppcx/begin-function.md) /  [End](../cppcx/end-function.md)([Windows:: Foundation:: Collections:: \<T> IVector](/uwp/api/windows.foundation.collections.ivector-1))|
|[Platform:: Collections:: VectorViewIterator\<T>](../cppcx/platform-collections-vectorviewiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IVectorView \<T> ](/uwp/api/windows.foundation.collections.ivectorview-1)^ i int).|[Rozpocznij](../cppcx/begin-function.md) /  [End](../cppcx/end-function.md) ([IVectorView \<T> ](/uwp/api/windows.foundation.collections.ivectorview-1)^)|
|[Platform:: Collections:: InputIterator\<T>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IIterator \<T> ](/uwp/api/windows.foundation.collections.iiterator-1)^ i T).|[Rozpocznij](../cppcx/begin-function.md) /  [End](../cppcx/end-function.md) ([IIterable \<T> ](/uwp/api/windows.foundation.collections.iiterable-1))|
|[Platform:: Collections:: InputIterator<IKeyValuePair\<K, V>^>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IIterator \<T> ](/uwp/api/windows.foundation.collections.iiterator-1)^ i T).|[Rozpocznij](../cppcx/begin-function.md) /  [End](../cppcx/end-function.md) ([IMAP \<K,V> ](/uwp/api/windows.foundation.collections.imap-2).|
|[Platform:: Collections:: InputIterator<IKeyValuePair\<K, V>^>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IIterator \<T> ](/uwp/api/windows.foundation.collections.iiterator-1)^ i T).|[Rozpocznij](../cppcx/begin-function.md) /  [End](../cppcx/end-function.md) ([Windows:: Foundation:: Collections:: IMapView](/uwp/api/windows.foundation.collections.imapview-2))|

### <a name="collection-change-events"></a>Zdarzenia zmiany kolekcji

`Vector` i `Map` obsługują powiązania danych w kolekcjach XAML przez zaimplementowanie zdarzeń, które pojawiają się, gdy obiekt kolekcji jest zmieniany lub resetowany, lub gdy dowolny element kolekcji zostanie wstawiony, usunięty lub zmieniony. Można napisać własne typy obsługujące DataBinding, chociaż nie można dziedziczyć z `Map` lub `Vector` ponieważ te typy są zapieczętowane.

Elementy [Windows:: Foundation:: Collections](/uwp/api/windows.foundation.collections.vectorchangedeventhandler-1) :: VectorChangedEventHandler i [Windows:: Foundation:: Collections:: MapChangedEventHandler](/uwp/api/windows.foundation.collections.mapchangedeventhandler-2) określają sygnatury obsługi zdarzeń dla zdarzeń zmiany kolekcji. Klasy [Windows:: Foundation:: Collections:: CollectionChange](/uwp/api/windows.foundation.collections.collectionchange) Public enum i `Platform::Collection::Details::MapChangedEventArgs` `Platform::Collections::Details::VectorChangedEventArgs` klasy ref, przechowują argumenty zdarzenia w celu ustalenia, co spowodowało zdarzenie. `*EventArgs`Typy są zdefiniowane w `Details` przestrzeni nazw, ponieważ nie trzeba ich tworzyć ani używać jawnie w przypadku używania `Map` lub `Vector` .

## <a name="see-also"></a>Zobacz też

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
