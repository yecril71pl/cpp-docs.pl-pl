---
title: Kolekcje (C++/CX)
ms.date: 11/19/2018
ms.assetid: 914da30b-aac5-4cd7-9da3-a5ac08cdd72c
ms.openlocfilehash: ff3fb9899355ec05083dc15c16d74c9aa1d3fd8f
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740317"
---
# <a name="collections-ccx"></a>Kolekcje (C++/CX)

W programie C++/CX można korzystać z bezpłatnych kontenerów biblioteki szablonów standardowych (STL) lub dowolnego innego typu kolekcji zdefiniowanego przez użytkownika. Jednak w przypadku przekazywania kolekcji z powrotem i w środowisko wykonawcze systemu Windows ramach interfejsu ABI aplikacji, na przykład do kontrolki XAML lub do klienta JavaScript — należy użyć środowisko wykonawcze systemu Windows typów kolekcji.

Środowisko wykonawcze systemu Windows definiuje interfejsy dla kolekcji i powiązanych typów, a C++/CX dostarcza konkretne C++ implementacje w pliku nagłówkowym kolekcji. h. Na tej ilustracji przedstawiono relacje między typami kolekcji:

![Drzewo&#43;&#43;&#47;dziedziczenia języka c dla typów kolekcji](../cppcx/media/cppcxcollectionsinheritancetree.png "c&#43;&#43;&#47;, drzewo dziedziczenia dla typów kolekcji")

- [Klasa platform:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) jest podobna do [klasy std:: Vector](../standard-library/vector-class.md).

- Klasa [platform:: Collections:: map](../cppcx/platform-collections-map-class.md) jest podobna do [klasy std:: map](../standard-library/map-class.md).

- [Platform:: Collections:: VectorView Class](../cppcx/platform-collections-vectorview-class.md) i[platform:: Collections:: MapView, Klasa](../cppcx/platform-collections-mapview-class.md) jest tylko do `Vector` odczytu `Map`wersji systemów i.

- Iteratory są zdefiniowane w [przestrzeni nazw platform:: Collections](../cppcx/platform-collections-namespace.md). Te Iteratory spełniają wymagania dla iteratorów STL i umożliwiają użycie [std:: find](../standard-library/algorithm-functions.md#find), [std:: count_if](../standard-library/algorithm-functions.md#count_if)i innych algorytmów STL w dowolnym [systemie Windows:: Foundation:: Collections](/uwp/api/windows.foundation.collections) Type lub [platform:: Collections](../cppcx/platform-collections-namespace.md) konkretny typ. Na przykład oznacza to, że można wykonać iterację kolekcji w składniku środowisko wykonawcze systemu Windows utworzonym w C# ramach i zastosować do niego algorytm STL.

   > [!IMPORTANT]
   > Iteratory `VectorIterator` serwerów proxy `VectorViewIterator` i wykorzystują `VectoryProxy<T>` obiekty `ArrowProxy<T>` proxy oraz umożliwiają korzystanie z kontenerów STL. Aby uzyskać więcej informacji, zobacz "elementy VectorProxy" w dalszej części tego artykułu.

- Typy C++kolekcji/CX obsługują te same gwarancje bezpieczeństwa wątku, które obsługują kontenery STL.

- [Windows:: Foundation:: Collections:: IObservableVector](/uwp/api/Windows.Foundation.Collections.IObservableVector_T_) i [Windows:: Foundation:: Collections:: IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) definiują zdarzenia, które są wywoływane, gdy kolekcja zostanie zmieniona na różne sposoby. Implementując te interfejsy, [platform:: Collections:: map](../cppcx/platform-collections-map-class.md) i [platform:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) obsługuje powiązanie danych z kolekcjami XAML. Na przykład jeśli masz `Vector` dane, które są powiązane `Grid`z danymi, po dodaniu elementu do kolekcji, zmiana jest odzwierciedlana w interfejsie użytkownika siatki.

## <a name="vector-usage"></a>Użycie wektora

Gdy klasa musi przekazać kontener sekwencyjny do innego składnika Środowisko wykonawcze systemu Windows, użyj [systemu Windows:: Foundation:: Collections:: IVector\<T >](/uwp/api/Windows.Foundation.Collections.IVector_T_) jako parametr lub typ zwracany, a [platforma:: Collections:: Vector\<T >](../cppcx/platform-collections-vector-class.md) jako konkretna implementacja. Jeśli spróbujesz użyć `Vector` typu w publicznej wartości zwracanej lub parametrze, zostanie zgłoszony błąd kompilatora C3986. Możesz naprawić ten błąd, zmieniając `Vector` element `IVector`na.

> [!IMPORTANT]
> Jeśli przekazujesz sekwencję w ramach własnego programu, użyj opcji `Vector` lub `std::vector` , ponieważ są one wydajniejsze niż `IVector`. Używaj `IVector` tylko w przypadku przekazywania kontenera między ABI.
>
> System typu środowisko wykonawcze systemu Windows nie obsługuje koncepcji tablic nieregularnych, dlatego nie można przekazać IVector < platform:: Array\<T > > jako wartości zwracanej lub parametru metody. Aby przekazać nieregularną tablicę lub sekwencję sekwencji w ramach ABI, użyj `IVector<IVector<T>^>`.

`Vector<T>`dostarcza metody, które są wymagane do dodawania, usuwania i uzyskiwania dostępu do elementów w kolekcji, a także niejawnie konwertowane na `IVector<T>`. Można również użyć algorytmów STL w wystąpieniach `Vector<T>`. W poniższym przykładzie przedstawiono podstawowe użycie. Funkcja [BEGIN Function](../cppcx/begin-function.md) i [End](../cppcx/end-function.md) `Platform::Collections` znajduje się w tym miejscu w przestrzeni nazw, `std` a nie w przestrzeni nazw.

[!code-cpp[cx_collections#01](../cppcx/codesnippet/CPP/collections/class1.cpp#01)]

Jeśli masz istniejący kod, który używa `std::vector` i chcesz ponownie użyć go w składniku środowisko wykonawcze systemu Windows, po prostu Użyj jednego `Vector` z konstruktorów przyjmujących `std::vector` lub parę iteratorów, aby skonstruować `Vector` w punkcie, w którym przeszedł Kolekcja przez ABI. Poniższy przykład pokazuje, `Vector` jak używać konstruktora przenoszenia do wydajnej inicjalizacji `std::vector`z. Po operacji przenoszenia oryginalna `vec` zmienna nie jest już prawidłowa.

[!code-cpp[cx_collections#02](../cppcx/codesnippet/CPP/collections/class1.cpp#02)]

Jeśli masz wektor ciągów, które muszą być przekazywane przez ABI w pewnym momencie w przyszłości, musisz zdecydować, czy należy utworzyć ciągi początkowo jako `std::wstring` typy, czy jako `Platform::String^` typy. Jeśli konieczne jest wykonanie wielu operacji przetwarzania ciągów, użyj `wstring`. W przeciwnym razie należy utworzyć ciągi `Platform::String^` jako typy i uniknąć kosztów ich późniejszego konwertowania. Należy również określić, czy te ciągi mają być umieszczane `std:vector` w `Platform::Collections::Vector` , czy wewnętrznie. Ogólnie rzecz biorąc, użyj `std::vector` , a następnie `Platform::Vector` Utwórz z niego tylko wtedy, gdy przekazujesz kontener przez ABI.

## <a name="value-types-in-vector"></a>Typy wartości w wektorze

Każdy element, który ma być przechowywany w [platformie:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) , musi obsługiwać porównanie równości (niejawnie lub przy użyciu niestandardowego [std:: equal_to](../standard-library/equal-to-struct.md) komparator). Wszystkie typy odwołań i wszystkie typy skalarne niejawnie obsługują porównania równości. Dla nieskalarnych typów wartości, takich jak [Windows:: Foundation::D atetime](/uwp/api/windows.foundation.datetime), lub na potrzeby niestandardowych porównań — `objA->UniqueID == objB->UniqueID`na przykład — należy podać obiekt funkcji niestandardowej.

## <a name="vectorproxy-elements"></a>Elementy VectorProxy

[Platform:: Collections:: VectorIterator](../cppcx/platform-collections-vectoriterator-class.md) i [platform:: Collections:: VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md) umożliwia korzystanie `range for` z pętli i algorytmów, takich jak [std:: sort](../standard-library/algorithm-functions.md#sort) z kontenerem [IVector\<T >](/uwp/api/Windows.Foundation.Collections.IVector_T_) . Ale `IVector` do elementów nie można uzyskać C++ dostępu za poorednictwem dereferencji wskaźnika. dostęp do nich można uzyskać tylko za poorednictwem metod [GetAt](/uwp/api/windows.foundation.collections.ivector-1.getat) i [SetAt](/uwp/api/windows.foundation.collections.ivector-1.setat) . W `Platform::Details::VectorProxy<T>` związku z tym Iteratory używają klas proxy i `Platform::Details::ArrowProxy<T>` zapewniają dostęp do poszczególnych elementów za pomocą __\*__ operatorów, __->__ i  __\[]__ , zgodnie z wymaganiami biblioteki standardowej. Mówiąc `IVector<Person^> vec`, `*begin(vec)` typ to`VectorProxy<Person^>`. Jednak obiekt proxy jest prawie zawsze przezroczysty dla kodu. Te obiekty proxy nie są udokumentowane, ponieważ są przeznaczone tylko do użytku wewnętrznego przez Iteratory, ale warto wiedzieć, jak działa mechanizm.

Jeśli używasz `range for` pętli przez `IVector` kontenery, użyj `auto&&` , aby włączyć zmienną iteratora w celu poprawnego `VectorProxy` powiązania do elementów. Jeśli używasz `auto` lub `auto&`, C4239 jest wywoływane Ostrzeżenie kompilatora i `VectoryProxy` jest ono wymienione w tekście ostrzegawczym.

Na poniższej ilustracji przedstawiono `range for` pętlę `IVector<Person^>`w. Zwróć uwagę, że wykonywanie zostało zatrzymane w punkcie przerwania w wierszu 64. Okno **QuickWatch** pokazuje, że zmienna `p` iteratora `VectorProxy<Person^>` jest w rzeczywistości, która ma `m_v` i `m_i` zmienne składowe. Jednak po wywołaniu `GetType` tej zmiennej zwraca identyczny typ `Person` do wystąpienia `p2`. Wnioskiem jest to, że `VectorProxy` chociaż `ArrowProxy` i mogą występować w **QuickWatch**, debuger niektórych błędów kompilatora lub inne miejsca, zazwyczaj nie trzeba jawnie kodu.

![VectorProxy w zakresie&#45;opartym na pętli](../cppcx/media/vectorproxy-1.png "VectorProxy w&#45;zakresie opartym na pętli")

Jeden scenariusz, w którym należy wykonać kod wokół obiektu serwera proxy, jest potrzebny do wykonania `dynamic_cast` na elementach — na przykład podczas wyszukiwania obiektów XAML określonego typu `UIElement` w kolekcji elementów. W takim przypadku należy najpierw rzutować element na [platformę:: Object](../cppcx/platform-object-class.md)^, a następnie wykonać dynamiczne rzutowanie:

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

Ten przykład pokazuje, jak wstawiać elementy i wyszukiwać je w [platformie:: Collections:: map](../cppcx/platform-collections-map-class.md), a następnie zwracać `Map` jako tylko do odczytu [Windows:: Foundation:: Collections:: IMapView]/UWP/API/Windows.Foundation.Collections.IMapView_K_V_) Wprowadź.

[!code-cpp[cx_collections#04](../cppcx/codesnippet/CPP/collections/class1.cpp#04)]

Ogólnie rzecz biorąc, w przypadku funkcji mapy wewnętrznej Preferuj `std::map` typ z przyczyn związanych z wydajnością. Jeśli konieczne jest przekazanie kontenera między ABI, należy skonstruować [platformę:: Collections:: map](../cppcx/platform-collections-map-class.md) z elementu [std:: map](../standard-library/map-class.md) `Map` i zwrócić jako [Windows:: Foundation:: Collections:: IMAP](/uwp/api/Windows.Foundation.Collections.IMap_K_V_). Jeśli spróbujesz użyć `Map` typu w publicznej wartości zwracanej lub parametrze, zostanie zgłoszony błąd kompilatora C3986. Możesz naprawić ten błąd, zmieniając `Map` element `IMap`na. W niektórych przypadkach — na przykład, jeśli nie tworzysz dużej liczby odnośników ani wstawień i przekazujesz kolekcję przez ABIe często — może być `Platform::Collections::Map` tańsze od początku i uniknąć kosztów konwersji `std::map`. W każdym przypadku należy unikać wyszukiwania i wstawiania operacji, ponieważ `IMap` są one najmniej zgodne z trzema typami. Konwertuj na `IMap` tylko w punkcie, w którym przeszedł kontener w ABI.

## <a name="value-types-in-map"></a>Typy wartości w mapowaniu

Elementy w elemencie [platform:: Collections:: map](../cppcx/platform-collections-map-class.md) są uporządkowane. Każdy element, który ma być przechowywany `Map` w, musi obsługiwać mniej niż porównanie z ścisłym nieprawidłowym porządkowaniem, niejawnie lub przy użyciu niestandardowego [STL:: less](../standard-library/less-struct.md) komparator. Typy skalarne obsługują porównanie niejawnie. W przypadku typów wartości nieskalarnych, `Windows::Foundation::DateTime`takich jak lub niestandardowych porównań — na `objA->UniqueID < objB->UniqueID`przykład — należy podać niestandardowy komparator.

## <a name="collection-types"></a>Typy kolekcji

Kolekcje dzielą się na cztery kategorie: modyfikowalne wersje i wersje tylko do odczytu kolekcji sekwencji i kolekcji asocjacyjnych. Ponadto C++/CX rozszerza kolekcje, dostarczając trzy klasy iteratorów, które upraszczają dostęp do kolekcji.

Elementy kolekcji modyfikowalnej można zmienić, ale elementy kolekcji tylko do odczytu, która jest znana jako *Widok*, można odczytać tylko. Elementy klasy [platform:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) lub[platform:: Collections:: VectorView](../cppcx/platform-collections-vectorview-class.md) można uzyskać dostępu przy użyciu iteratora lub [wektora kolekcji:: GetAt](../cppcx/platform-collections-vector-class.md#getat) i indeksu. Do elementów kolekcji asocjacyjnej można uzyskać dostęp za pomocą [mapy kolekcji:: Lookup](../cppcx/platform-collections-map-class.md#lookup) i klucza.

[Platform::Collections::Map, klasa](../cppcx/platform-collections-map-class.md)<br/>
Modyfikowalna kolekcja asocjacyjna. Elementy mapy to pary klucz-wartość. Wyszukiwanie klucza w celu pobrania jego skojarzonej wartości i przechodzenia przez wszystkie pary klucz-wartość są obsługiwane.

`Map`i `MapView` są szablonem. `<K, V, C = std::less<K>>`w związku z tym można dostosować komparator.  `<T, E = std::equal_to<T>>` `IndexOf()`Ponadto i są`VectorView` szablonami w programie, aby można było dostosować zachowanie programu. `Vector` Jest to ważne głównie dla `Vector` struktur `VectorView` wartości i. Na przykład, aby utworzyć wektor\<Windows:: Foundation::D atetime >, należy podać niestandardowy komparator, ponieważ DateTime nie przeciąża operatora = =.

[Platform::Collections::MapView, klasa](../cppcx/platform-collections-mapview-class.md)<br/>
Wersja programu `Map`.

[Platform::Collections::Vector, klasa](../cppcx/platform-collections-vector-class.md)<br/>
Modyfikowalna kolekcja sekwencji. `Vector<T>`Program obsługuje dostęp losowy do czasu stałego oraz operacje [dołączania](../cppcx/platform-collections-vector-class.md#append) w czasie stałym.

[Platform::Collections::VectorView, klasa](../cppcx/platform-collections-vectorview-class.md)<br/>
Wersja programu `Vector`.

[Platform::Collections::InputIterator, klasa](../cppcx/platform-collections-inputiterator-class.md)<br/>
Iterator STL, który spełnia wymagania iteratora wejściowego STL.

[Platform::Collections::VectorIterator, klasa](../cppcx/platform-collections-vectoriterator-class.md)<br/>
Iterator STL, który spełnia wymagania dla iteratora dostęp swobodny STL.

[Platform::Collections::VectorViewIterator, klasa](../cppcx/platform-collections-vectorviewiterator-class.md)<br/>
Iterator STL, który spełnia wymagania iteratora dostępu swobodnego STL `const` .

### <a name="begin-and-end-functions"></a>funkcje Begin () i End ()

`Vector`Aby uprościć użycie STL do przetwarzania, `MapView` `VectorView`, `Map`, `Windows::Foundation::Collections` i dowolnych obiektów,/CX C++obsługuje przeciążenia [funkcji BEGIN](../cppcx/begin-function.md) i [End Function](../cppcx/end-function.md) , która nie jest elementem członkowskim obowiązki.

Poniższa tabela zawiera listę dostępnych iteratorów i funkcji.

|Iteratory|Funkcje|
|---------------|---------------|
|[Platform:: Collections::\<VectorIterator T >](../cppcx/platform-collections-vectoriterator-class.md)<br /><br /> (Wewnętrznie przechowuje [system Windows:: Foundation:: Collections:: IVector\<T >](/uwp/api/Windows.Foundation.Collections.IVector_T_) i int.)|[BEGIN](../cppcx/begin-function.md)/ [](../cppcx/end-function.md)End([Windows:: Foundation:: Collections:: IVector\<T >](/uwp/api/Windows.Foundation.Collections.IVector_T_))|
|[Platform:: Collections::\<VectorViewIterator T >](../cppcx/platform-collections-vectorviewiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IVectorView\<T >](/uwp/api/Windows.Foundation.Collections.IVectorView_T_)^ i int).|[](../cppcx/begin-function.md)początek/ [końca](../cppcx/end-function.md) ([IVectorViewT\<>](/uwp/api/Windows.Foundation.Collections.IVectorView_T_)^)|
|[Platform:: Collections::\<InputIterator T >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IIterator\<T >](/uwp/api/Windows.Foundation.Collections.IIterator_T_)^ i T).|[](../cppcx/begin-function.md)Begin/ [End](../cppcx/end-function.md) ([IIterableT\<>](/uwp/api/Windows.Foundation.Collections.IIterable_T_))|
|[Platform:: Collections:: InputIterator <\<IKeyValuePair K, V > ^ >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IIterator\<T >](/uwp/api/Windows.Foundation.Collections.IIterator_T_)^ i T).|[](../cppcx/begin-function.md)Rozpocznij/ [zakończenie](../cppcx/end-function.md) ([IMAPK\<, V >](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).|
|[Platform:: Collections:: InputIterator <\<IKeyValuePair K, V > ^ >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IIterator\<T >](/uwp/api/Windows.Foundation.Collections.IIterator_T_)^ i T).|[](../cppcx/begin-function.md)Begin/ [End](../cppcx/end-function.md) ([Windows:: Foundation:: Collections:: IMapView]/UWP/API/Windows.Foundation.Collections.IMapView_K_V_))|

### <a name="collection-change-events"></a>Zdarzenia zmiany kolekcji

`Vector`i `Map` obsługują powiązania danych w kolekcjach XAML przez zaimplementowanie zdarzeń, które pojawiają się, gdy obiekt kolekcji jest zmieniany lub resetowany, lub gdy dowolny element kolekcji zostanie wstawiony, usunięty lub zmieniony. Można napisać własne typy obsługujące DataBinding, chociaż nie można dziedziczyć z `Map` lub `Vector` ponieważ te typy są zapieczętowane.

Elementy [Windows:: Foundation:: Collections](/uwp/api/windows.foundation.collections.vectorchangedeventhandler) :: VectorChangedEventHandler i [Windows:: Foundation:: Collections:: MapChangedEventHandler](/uwp/api/windows.foundation.collections.mapchangedeventhandler) określają sygnatury obsługi zdarzeń dla zdarzeń zmiany kolekcji. Klasy [Windows:: Foundation:: Collections:: CollectionChange](/uwp/api/windows.foundation.collections.collectionchange) Public enum i `Platform::Collection::Details::MapChangedEventArgs` `Platform::Collections::Details::VectorChangedEventArgs` klasy ref, przechowują argumenty zdarzenia w celu ustalenia, co spowodowało zdarzenie. Typy są zdefiniowane w przestrzeni nazw `Details` , ponieważ nie trzeba ich tworzyć ani używać jawnie w przypadku używania `Map` lub `Vector`. `*EventArgs`

## <a name="see-also"></a>Zobacz także

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
