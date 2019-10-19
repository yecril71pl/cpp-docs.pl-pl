---
title: Kolekcje (C++/CX)
ms.date: 11/19/2018
ms.assetid: 914da30b-aac5-4cd7-9da3-a5ac08cdd72c
ms.openlocfilehash: ff3fb9899355ec05083dc15c16d74c9aa1d3fd8f
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "70740317"
---
# <a name="collections-ccx"></a>Kolekcje (C++/CX)

W programie C++/CX można korzystać z bezpłatnych kontenerów biblioteki szablonów standardowych (STL) lub dowolnego innego typu kolekcji zdefiniowanego przez użytkownika. Jednak w przypadku przekazywania kolekcji z powrotem i w środowisko wykonawcze systemu Windows ramach interfejsu ABI aplikacji, na przykład do kontrolki XAML lub do klienta JavaScript — należy użyć środowisko wykonawcze systemu Windows typów kolekcji.

Środowisko wykonawcze systemu Windows definiuje interfejsy dla kolekcji i powiązanych typów, a C++/CX dostarcza konkretne C++ implementacje w pliku nagłówkowym kolekcji. h. Na tej ilustracji przedstawiono relacje między typami kolekcji:

![Drzewo&#43;&#43;&#47;dziedziczenia języka C dla typów kolekcji](../cppcx/media/cppcxcollectionsinheritancetree.png "Drzewo&#43;&#43;&#47;dziedziczenia języka C dla typów kolekcji")

- [Klasa platform:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) jest podobna do [klasy std:: Vector](../standard-library/vector-class.md).

- Klasa [platform:: Collections:: map](../cppcx/platform-collections-map-class.md) jest podobna do [klasy std:: map](../standard-library/map-class.md).

- [Platform:: Collections:: VectorView Class](../cppcx/platform-collections-vectorview-class.md) and[platform:: Collections:: MapView, klasy](../cppcx/platform-collections-mapview-class.md) `Vector` i `Map`.

- Iteratory są zdefiniowane w [przestrzeni nazw platform:: Collections](../cppcx/platform-collections-namespace.md). Te Iteratory spełniają wymagania dla iteratorów STL i umożliwiają użycie [std:: find](../standard-library/algorithm-functions.md#find), [std:: count_if](../standard-library/algorithm-functions.md#count_if)i innych algorytmów STL w dowolnym [systemie Windows:: Foundation:: Collections](/uwp/api/windows.foundation.collections) Type lub [platform:: Collections](../cppcx/platform-collections-namespace.md) konkretny typ. Na przykład oznacza to, że można wykonać iterację kolekcji w składniku środowisko wykonawcze systemu Windows utworzonym w C# ramach i zastosować do niego algorytm STL.

   > [!IMPORTANT]
   > Iteratory serwerów proxy `VectorIterator` i `VectorViewIterator` używają obiektów serwera proxy `VectoryProxy<T>` i `ArrowProxy<T>`, aby umożliwić użycie z kontenerami STL. Aby uzyskać więcej informacji, zobacz "elementy VectorProxy" w dalszej części tego artykułu.

- Typy C++kolekcji/CX obsługują te same gwarancje bezpieczeństwa wątku, które obsługują kontenery STL.

- [Windows:: Foundation:: Collections:: IObservableVector](/uwp/api/Windows.Foundation.Collections.IObservableVector_T_) i [Windows:: Foundation:: Collections:: IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) definiują zdarzenia, które są wywoływane, gdy kolekcja zostanie zmieniona na różne sposoby. Implementując te interfejsy, [platform:: Collections:: map](../cppcx/platform-collections-map-class.md) i [platform:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) obsługuje powiązanie danych z kolekcjami XAML. Na przykład jeśli masz `Vector`, który jest powiązany z danymi `Grid`, po dodaniu elementu do kolekcji, zmiana zostanie odzwierciedlona w interfejsie użytkownika siatki.

## <a name="vector-usage"></a>Użycie wektora

Gdy klasa musi przekazać kontener sekwencji do innego składnika środowisko wykonawcze systemu Windows, użyj funkcji [Windows:: Foundation:: Collections:: IVector \<T >](/uwp/api/Windows.Foundation.Collections.IVector_T_) jako parametru lub typu zwracanego, a [platforma:: Collections:: Vector \<T >](../cppcx/platform-collections-vector-class.md) jako konkretna implementacja. Jeśli spróbujesz użyć `Vector` typu w publicznej wartości zwracanej lub parametrze, zostanie zgłoszony błąd kompilatora C3986. Możesz naprawić ten błąd, zmieniając `Vector` na `IVector`.

> [!IMPORTANT]
> Jeśli przekazujesz sekwencję w ramach własnego programu, użyj `Vector` lub `std::vector`, ponieważ są one wydajniejsze niż `IVector`. Używaj `IVector` tylko wtedy, gdy przekazujesz kontener w ABI.
>
> System typu środowisko wykonawcze systemu Windows nie obsługuje koncepcji tablic nieregularnych i dlatego nie można przekazać klasy IVector < platform:: Array \<T > > jako wartości zwracanej lub parametru metody. Aby przekazać nieregularną tablicę lub sekwencję sekwencji w ramach ABI, użyj `IVector<IVector<T>^>`.

`Vector<T>` udostępnia metody, które są wymagane do dodawania, usuwania i uzyskiwania dostępu do elementów w kolekcji, a także niejawnie konwertowane na `IVector<T>`. Można również użyć algorytmów STL w wystąpieniach `Vector<T>`. W poniższym przykładzie przedstawiono podstawowe użycie. Funkcja [BEGIN Function](../cppcx/begin-function.md) i [End](../cppcx/end-function.md) znajduje się w tym miejscu z przestrzeni nazw `Platform::Collections`, a nie przestrzeni nazw `std`.

[!code-cpp[cx_collections#01](../cppcx/codesnippet/CPP/collections/class1.cpp#01)]

Jeśli masz istniejący kod, który używa `std::vector` i chcesz ponownie użyć go w składniku środowisko wykonawcze systemu Windows, po prostu Użyj jednego z konstruktorów `Vector`, które pobierają `std::vector` lub parę iteratorów w celu skonstruowania `Vector` w punkcie, w którym została przekazana kolekcja w ABI. Poniższy przykład pokazuje, jak użyć konstruktora przenoszenia `Vector` do wydajnej inicjalizacji z `std::vector`. Po operacji przenoszenia oryginalna zmienna `vec` nie jest już prawidłowa.

[!code-cpp[cx_collections#02](../cppcx/codesnippet/CPP/collections/class1.cpp#02)]

Jeśli masz wektor ciągów, które muszą być przekazywane przez ABI w pewnym momencie w przyszłości, musisz zdecydować, czy należy utworzyć ciągi początkowo jako typy `std::wstring`, czy jako typy `Platform::String^`. Jeśli konieczne jest wykonanie wielu operacji przetwarzania ciągów, użyj `wstring`. W przeciwnym razie należy utworzyć ciągi jako typy `Platform::String^` i uniknąć kosztów ich późniejszego konwertowania. Należy również zdecydować, czy te ciągi mają być umieszczane w `std:vector`, czy `Platform::Collections::Vector` wewnętrznie. Ogólnie rzecz biorąc, użyj `std::vector` a następnie utwórz `Platform::Vector` z niego tylko wtedy, gdy przekazujesz kontener przez ABI.

## <a name="value-types-in-vector"></a>Typy wartości w wektorze

Każdy element, który ma być przechowywany w [platformie:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) , musi obsługiwać porównanie równości (niejawnie lub przy użyciu niestandardowego [std:: equal_to](../standard-library/equal-to-struct.md) komparator). Wszystkie typy odwołań i wszystkie typy skalarne niejawnie obsługują porównania równości. Dla nieskalarnych typów wartości, takich jak [Windows:: Foundation::D atetime](/uwp/api/windows.foundation.datetime), lub dla niestandardowych porównań — na przykład `objA->UniqueID == objB->UniqueID` — należy podać obiekt funkcji niestandardowej.

## <a name="vectorproxy-elements"></a>Elementy VectorProxy

[Platform:: Collections:: VectorIterator](../cppcx/platform-collections-vectoriterator-class.md) i [platform:: Collections:: VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md) umożliwia korzystanie z `range for` pętle i algorytmy, takie jak [std:: sort](../standard-library/algorithm-functions.md#sort) z kontenerem [IVector \<T >](/uwp/api/Windows.Foundation.Collections.IVector_T_) . Ale nie można uzyskać dostępu do `IVector` C++ elementów za poorednictwem dereferencji wskaźnika; dostęp do nich można uzyskać tylko za poorednictwem metod [GetAt](/uwp/api/windows.foundation.collections.ivector-1.getat) i [SetAt](/uwp/api/windows.foundation.collections.ivector-1.setat) . W związku z tym Iteratory używają klas proxy `Platform::Details::VectorProxy<T>` i `Platform::Details::ArrowProxy<T>` do zapewnienia dostępu do poszczególnych elementów za pomocą operatorów __\*__ , __->__ i __\[]__ , zgodnie z wymaganiami biblioteki standardowej. Dokładnie mówiąc, biorąc pod `IVector<Person^> vec`, typ `*begin(vec)` jest `VectorProxy<Person^>`. Jednak obiekt proxy jest prawie zawsze przezroczysty dla kodu. Te obiekty proxy nie są udokumentowane, ponieważ są przeznaczone tylko do użytku wewnętrznego przez Iteratory, ale warto wiedzieć, jak działa mechanizm.

W przypadku używania pętli `range for` za pośrednictwem kontenerów `IVector` należy użyć polecenia `auto&&`, aby umożliwić zmiennej iterator prawidłowo powiązać ją z elementami `VectorProxy`. Jeśli używasz `auto` lub `auto&`, zostanie zgłoszone ostrzeżenie kompilatora C4239, a `VectoryProxy` jest wymieniony w tekście ostrzegawczym.

Na poniższej ilustracji przedstawiono pętlę `range for`ą w `IVector<Person^>`. Zwróć uwagę, że wykonywanie zostało zatrzymane w punkcie przerwania w wierszu 64. Okno **QuickWatch** pokazuje, że zmienna iteratora `p` jest w rzeczywistości `VectorProxy<Person^>`, która ma `m_v` i `m_i` zmienne składowe. Jednak w przypadku wywołania `GetType` na tej zmiennej zwraca identyczny typ do wystąpienia `Person` `p2`. Wnioskiem polega na tym, że chociaż `VectorProxy` i `ArrowProxy` mogą pojawić się w **QuickWatch**, debuger niektórych błędów kompilatora lub inne miejsca, zazwyczaj nie trzeba go jawnie zakodować.

![VectorProxy w zakresie&#45;opartym na pętli](../cppcx/media/vectorproxy-1.png "VectorProxy w zakresie&#45;opartym na pętli")

Jeden scenariusz, w którym należy wykonać kod wokół obiektu proxy, jest w sytuacji, gdy konieczne jest wykonanie `dynamic_cast` na elementach — na przykład podczas wyszukiwania obiektów XAML określonego typu w kolekcji elementów `UIElement`. W takim przypadku należy najpierw rzutować element na [platformę:: Object](../cppcx/platform-object-class.md)^, a następnie wykonać dynamiczne rzutowanie:

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

Ten przykład pokazuje, jak wstawiać elementy i wyszukiwać je w [platformie:: Collections:: map](../cppcx/platform-collections-map-class.md), a następnie zwracać `Map` jako typ tylko do odczytu [Windows:: Foundation:: Collections:: IMapView]/UWP/API/Windows.Foundation.Collections.IMapView_K_V_).

[!code-cpp[cx_collections#04](../cppcx/codesnippet/CPP/collections/class1.cpp#04)]

Ogólnie rzecz biorąc, w przypadku funkcji mapy wewnętrznej Preferuj typ `std::map` ze względu na wydajność. Jeśli konieczne jest przekazanie kontenera między ABI, konstrukcja [platform:: Collections:: map](../cppcx/platform-collections-map-class.md) z wartości [std:: map](../standard-library/map-class.md) i zwrócenia `Map` jako [Windows:: Foundation:: Collections:: IMAP](/uwp/api/Windows.Foundation.Collections.IMap_K_V_). Jeśli spróbujesz użyć `Map` typu w publicznej wartości zwracanej lub parametrze, zostanie zgłoszony błąd kompilatora C3986. Możesz naprawić ten błąd, zmieniając `Map` na `IMap`. W niektórych przypadkach — na przykład, jeśli nie tworzysz dużej liczby odnośników ani wstawień i przekazujesz kolekcję przez ABI często — może być tańsze użycie `Platform::Collections::Map` od początku i uniknięcie kosztu konwersji `std::map`. W każdym przypadku należy unikać wyszukiwania i wstawiania operacji na `IMap`, ponieważ są one najmniej zgodne z trzema typami. Konwertuj na `IMap` tylko w momencie przekazania kontenera między ABI.

## <a name="value-types-in-map"></a>Typy wartości w mapowaniu

Elementy w elemencie [platform:: Collections:: map](../cppcx/platform-collections-map-class.md) są uporządkowane. Każdy element, który ma być przechowywany w `Map` musi obsługiwać porównanie mniejsze niż w przypadku ścisłej słabej kolejności, niejawnie lub przy użyciu niestandardowego [STL:: less](../standard-library/less-struct.md) komparator. Typy skalarne obsługują porównanie niejawnie. Dla nieskalarnych typów wartości, takich jak `Windows::Foundation::DateTime`, lub niestandardowych porównań — na przykład `objA->UniqueID < objB->UniqueID` — należy podać niestandardowy komparator.

## <a name="collection-types"></a>Typy kolekcji

Kolekcje dzielą się na cztery kategorie: modyfikowalne wersje i wersje tylko do odczytu kolekcji sekwencji i kolekcji asocjacyjnych. Ponadto C++/CX rozszerza kolekcje, dostarczając trzy klasy iteratorów, które upraszczają dostęp do kolekcji.

Elementy kolekcji modyfikowalnej można zmienić, ale elementy kolekcji tylko do odczytu, która jest znana jako *Widok*, można odczytać tylko. Elementy klasy [platform:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) lub[platform:: Collections:: VectorView](../cppcx/platform-collections-vectorview-class.md) można uzyskać dostępu przy użyciu iteratora lub [wektora kolekcji:: GetAt](../cppcx/platform-collections-vector-class.md#getat) i indeksu. Do elementów kolekcji asocjacyjnej można uzyskać dostęp za pomocą [mapy kolekcji:: Lookup](../cppcx/platform-collections-map-class.md#lookup) i klucza.

[Platform::Collections::Map, klasa](../cppcx/platform-collections-map-class.md)<br/>
Modyfikowalna kolekcja asocjacyjna. Elementy mapy to pary klucz-wartość. Wyszukiwanie klucza w celu pobrania jego skojarzonej wartości i przechodzenia przez wszystkie pary klucz-wartość są obsługiwane.

`Map` i `MapView` są szablonem na `<K, V, C = std::less<K>>`; w związku z tym można dostosować komparator.  Ponadto `Vector` i `VectorView` są szablonami w `<T, E = std::equal_to<T>>`, aby można było dostosować zachowanie `IndexOf()`. Jest to szczególnie ważne w przypadku `Vector` i `VectorView` struktur wartości. Na przykład, aby utworzyć wektor \<Windows:: Foundation::D ateTime >, należy podać niestandardowy komparator, ponieważ DateTime nie przeciąża operatora = =.

[Platform::Collections::MapView, klasa](../cppcx/platform-collections-mapview-class.md)<br/>
Wersja `Map` tylko do odczytu.

[Platform::Collections::Vector, klasa](../cppcx/platform-collections-vector-class.md)<br/>
Modyfikowalna kolekcja sekwencji. `Vector<T>` obsługuje dostęp losowy do czasu stałego oraz operacje [dołączania](../cppcx/platform-collections-vector-class.md#append) do czasu stałych.

[Platform::Collections::VectorView, klasa](../cppcx/platform-collections-vectorview-class.md)<br/>
Wersja `Vector` tylko do odczytu.

[Platform::Collections::InputIterator, klasa](../cppcx/platform-collections-inputiterator-class.md)<br/>
Iterator STL, który spełnia wymagania iteratora wejściowego STL.

[Platform::Collections::VectorIterator, klasa](../cppcx/platform-collections-vectoriterator-class.md)<br/>
Iterator STL, który spełnia wymagania dla iteratora dostęp swobodny STL.

[Platform::Collections::VectorViewIterator, klasa](../cppcx/platform-collections-vectorviewiterator-class.md)<br/>
Iterator STL, który spełnia wymagania `const` Iterator dostępu swobodnego.

### <a name="begin-and-end-functions"></a>funkcje Begin () i End ()

Aby uprościć korzystanie z STL do przetwarzania `Vector`, `VectorView`, `Map`, `MapView` i dowolnych obiektów `Windows::Foundation::Collections`, C++/CX obsługuje przeciążenia [funkcji BEGIN](../cppcx/begin-function.md) i [funkcje, które](../cppcx/end-function.md) nie są elementami członkowskimi.

Poniższa tabela zawiera listę dostępnych iteratorów i funkcji.

|Iteratory|Funkcje|
|---------------|---------------|
|[Platform:: Collections:: VectorIterator \<T >](../cppcx/platform-collections-vectoriterator-class.md)<br /><br /> (Wewnętrznie przechowuje [system Windows:: Foundation:: Collections:: IVector \<T >](/uwp/api/Windows.Foundation.Collections.IVector_T_) i int).|[rozpocznij](../cppcx/begin-function.md) / [zakończenia](../cppcx/end-function.md)([Windows:: Foundation:: collections:: IVector \<T >](/uwp/api/Windows.Foundation.Collections.IVector_T_))|
|[Platform:: Collections:: VectorViewIterator \<T >](../cppcx/platform-collections-vectorviewiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IVectorView \<T >](/uwp/api/Windows.Foundation.Collections.IVectorView_T_)^ i int).|[rozpocznij](../cppcx/begin-function.md) / [zakończenia](../cppcx/end-function.md) ([IVectorView \<T >](/uwp/api/Windows.Foundation.Collections.IVectorView_T_)^)|
|[Platform:: Collections:: InputIterator \<T >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IIterator \<T >](/uwp/api/Windows.Foundation.Collections.IIterator_T_)^ i t).|[rozpocznij](../cppcx/begin-function.md) / [zakończenia](../cppcx/end-function.md) ([IIterable \<T >](/uwp/api/Windows.Foundation.Collections.IIterable_T_))|
|[Platform:: Collections:: InputIterator < IKeyValuePair \<K, V > ^ >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IIterator \<T >](/uwp/api/Windows.Foundation.Collections.IIterator_T_)^ i t).|[rozpocznij](../cppcx/begin-function.md) / [zakończenia](../cppcx/end-function.md) ([\<K IMAP, >](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).|
|[Platform:: Collections:: InputIterator < IKeyValuePair \<K, V > ^ >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IIterator \<T >](/uwp/api/Windows.Foundation.Collections.IIterator_T_)^ i t).|[rozpoczęcie](../cppcx/begin-function.md) / [zakończenia](../cppcx/end-function.md) ([Windows:: Foundation:: Collections:: IMapView]/UWP/API/Windows.Foundation.Collections.IMapView_K_V_))|

### <a name="collection-change-events"></a>Zdarzenia zmiany kolekcji

`Vector` i `Map` obsługują powiązania danych w kolekcjach XAML przez zaimplementowanie zdarzeń, które wystąpiły, gdy obiekt kolekcji zostanie zmieniony lub zresetowany lub gdy dowolny element kolekcji zostanie wstawiony, usunięty lub zmieniony. Można napisać własne typy obsługujące DataBinding, chociaż nie można dziedziczyć po `Map` lub `Vector`, ponieważ te typy są zapieczętowane.

Elementy [Windows:: Foundation:: Collections](/uwp/api/windows.foundation.collections.vectorchangedeventhandler) :: VectorChangedEventHandler i [Windows:: Foundation:: Collections:: MapChangedEventHandler](/uwp/api/windows.foundation.collections.mapchangedeventhandler) określają sygnatury obsługi zdarzeń dla zdarzeń zmiany kolekcji. [System Windows:: Foundation:: Kolekcje:: CollectionChange](/uwp/api/windows.foundation.collections.collectionchange) Public enum Class oraz klasy ref `Platform::Collection::Details::MapChangedEventArgs` i `Platform::Collections::Details::VectorChangedEventArgs`, przechowują argumenty zdarzeń, aby określić, co spowodowało zdarzenie. Typy `*EventArgs` są zdefiniowane w przestrzeni nazw `Details`, ponieważ nie trzeba ich tworzyć ani używać jawnie w przypadku używania `Map` lub `Vector`.

## <a name="see-also"></a>Zobacz także

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
