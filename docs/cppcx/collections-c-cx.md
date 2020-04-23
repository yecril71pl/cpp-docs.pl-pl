---
title: Kolekcje (C++/CX)
ms.date: 11/19/2018
ms.assetid: 914da30b-aac5-4cd7-9da3-a5ac08cdd72c
ms.openlocfilehash: 59e73b803a0878e88361c7fe75cff556b8eeedcd
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032320"
---
# <a name="collections-ccx"></a>Kolekcje (C++/CX)

W programie C++/CX można bezpłatnie korzystać z kontenerów standardowej biblioteki szablonów (STL) lub dowolnego innego typu kolekcji zdefiniowanego przez użytkownika. Jednak po przekazywaniu kolekcji między i z powrotem przez interfejs binarny aplikacji środowiska wykonawczego systemu Windows (ABI) — na przykład do formantu XAML lub do klienta JavaScript — należy użyć typów kolekcji środowiska wykonawczego systemu Windows.

Środowisko wykonawcze systemu Windows definiuje interfejsy dla kolekcji i typów pokrewnych, a C++/CX udostępnia konkretne implementacje języka C++ w pliku nagłówka collection.h. Na ilustracji przedstawiono relacje między typami kolekcji:

![C&#43;&#43;&#47;drzewa dziedziczenia CX dla typów kolekcji](../cppcx/media/cppcxcollectionsinheritancetree.png "C&#43;&#43;&#47;drzewa dziedziczenia CX dla typów kolekcji")

- Klasa [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) przypomina [klasę std::vector.](../standard-library/vector-class.md)

- [Klasa platform::Collections::Map Class](../cppcx/platform-collections-map-class.md) przypomina klasę [std::map.](../standard-library/map-class.md)

- [Platforma::Kolekcje::VectorView Klasa](../cppcx/platform-collections-vectorview-class.md) i[Platforma::Kolekcje::Klasa MapView](../cppcx/platform-collections-mapview-class.md) są `Vector` `Map`tylko do odczytu wersje i .

- Iteratory są zdefiniowane w [platformie::Obszar nazw kolekcji](../cppcx/platform-collections-namespace.md). Te iteratory spełniają wymagania dla iteratorów STL i umożliwiają użycie [std::find](../standard-library/algorithm-functions.md#find), [std::count_if](../standard-library/algorithm-functions.md#count_if)i innych algorytmów STL w dowolnym [systemie Windows::Foundation::Collections](/uwp/api/windows.foundation.collections) typu interfejsu lub [platformy::Kolekcje](../cppcx/platform-collections-namespace.md) typu betonu. Na przykład oznacza to, że można iterować kolekcji w składniku środowiska wykonawczego systemu Windows, który jest tworzony w języku C# i zastosować algorytm STL do niego.

   > [!IMPORTANT]
   > Iteratory proxy `VectorIterator` `VectorViewIterator` i korzystać `VectoryProxy<T>` `ArrowProxy<T>` z obiektów serwera proxy i włączyć użycie z kontenerów STL. Aby uzyskać więcej informacji, zobacz "VectorProxy elementów" w dalszej części tego artykułu.

- Typy kolekcji C++/CX obsługują te same gwarancje bezpieczeństwa wątków, które obsługują kontenery STL.

- [Windows::Foundation::Collections::IObservableVector](/uwp/api/windows.foundation.collections.iobservablevector-1) i [Windows::Foundation:Collections::IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2) definiują zdarzenia, które są uruchamiane, gdy kolekcja zmienia się na różne sposoby. Implementując te interfejsy, [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) i [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) obsługuje powiązania danych z kolekcjami XAML. Na przykład jeśli `Vector` masz, który jest powiązany z danymi `Grid`, po dodaniu elementu do kolekcji, zmiana jest odzwierciedlona w interfejsie sieci.

## <a name="vector-usage"></a>Użycie wektora

Gdy klasa ma przekazać kontener sekwencji do innego składnika środowiska wykonawczego systemu Windows, należy użyć [systemu Windows::Foundation::Collections:: IVector\<T>](/uwp/api/windows.foundation.collections.ivector-1) jako parametr lub typ zwracany i [Platform::Collections::Vector\<T>](../cppcx/platform-collections-vector-class.md) jako konkretnej implementacji. Jeśli spróbujesz `Vector` użyć typu w public return wartość lub parametr, błąd kompilatora C3986 zostanie podniesiona. Błąd można naprawić, zmieniając `Vector` wartość `IVector`na .

> [!IMPORTANT]
> Jeśli przekazujesz sekwencję we własnym programie, `Vector` użyj `std::vector` jednego lub ponieważ `IVector`są one bardziej wydajne niż . Używaj `IVector` tylko wtedy, gdy przekazujesz kontener przez ABI.
>
> System typu środowiska wykonawczego systemu Windows nie obsługuje koncepcji postrzępionych tablic i dlatego nie można przekazać\<IVector<Platform::Array T>> jako wartość zwracaną lub parametr metody. Aby przekazać postrzępioną tablicę lub sekwencję `IVector<IVector<T>^>`sekwencji w całej ABI, użyj .

`Vector<T>`zawiera metody, które są wymagane do dodawania, usuwania i uzyskiwania dostępu do `IVector<T>`elementów w kolekcji i jest niejawnie konwertowane na . Można również użyć algorytmów STL `Vector<T>`w wystąpieniach . W poniższym przykładzie przedstawiono niektóre podstawowe użycie. [Funkcja begin](../cppcx/begin-function.md) i [end w](../cppcx/end-function.md) `Platform::Collections` tym miejscu są `std` z obszaru nazw, a nie obszaru nazw.

[!code-cpp[cx_collections#01](../cppcx/codesnippet/CPP/collections/class1.cpp#01)]

Jeśli masz istniejący kod, który `std::vector` używa i chcesz go ponownie użyć w składniku środowiska wykonawczego systemu Windows, wystarczy użyć jednego z `Vector` konstruktorów, który zajmuje `std::vector` lub parę iteratorów do konstruowania `Vector` w punkcie, w którym przekazujesz kolekcję przez ABI. W poniższym przykładzie `Vector` pokazano, jak używać konstruktora przenoszenia do efektywnego inicjowania z . `std::vector` Po operacji przenoszenia `vec` oryginalna zmienna nie jest już prawidłowa.

[!code-cpp[cx_collections#02](../cppcx/codesnippet/CPP/collections/class1.cpp#02)]

Jeśli masz wektor ciągów, które muszą przejść przez ABI w pewnym momencie w przyszłości, `std::wstring` należy zdecydować, czy utworzyć ciągi początkowo jako typy lub jako `Platform::String^` typy. Jeśli musisz zrobić dużo przetwarzania na ciągach, `wstring`a następnie użyć . W przeciwnym razie należy `Platform::String^` utworzyć ciągi jako typy i uniknąć kosztów konwersji ich później. Należy również zdecydować, czy umieścić te `std:vector` `Platform::Collections::Vector` ciągi w lub wewnętrznie. Zgodnie z ogólną `std::vector` praktyką `Platform::Vector` należy użyć, a następnie utworzyć z niego tylko po przełknięciu kontenera przez ABI.

## <a name="value-types-in-vector"></a>Typy wartości w wektorze

Każdy element, który ma być przechowywany w [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) musi obsługiwać porównanie równości, niejawnie lub przy użyciu niestandardowego [komparatora std::equal_to,](../standard-library/equal-to-struct.md) który podasz. Wszystkie typy odwołań i wszystkie typy skalarne niejawnie obsługują porównania równości. W przypadku typów wartości innych niż skalarne, takich jak [Windows::Foundation::DateTime,](/uwp/api/windows.foundation.datetime)lub dla porównań niestandardowych — `objA->UniqueID == objB->UniqueID`na przykład — należy podać obiekt funkcji niestandardowej.

## <a name="vectorproxy-elements"></a>Elementy VectorProxy

[Platforma::Kolekcje::VectorIterator](../cppcx/platform-collections-vectoriterator-class.md) i [Platforma::Kolekcje::VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md) umożliwiają `range for` korzystanie z pętli i algorytmów, takich jak [std::sort](../standard-library/algorithm-functions.md#sort) z kontenerem [>IVector\<T.](/uwp/api/windows.foundation.collections.ivector-1) Ale `IVector` elementy nie mogą być dostępne za pośrednictwem wyłuskania wskaźnika języka C++; dostępne są tylko za pośrednictwem [metod GetAt](/uwp/api/windows.foundation.collections.ivector-1.getat) i [SetAt.](/uwp/api/windows.foundation.collections.ivector-1.setat) W związku z tym `Platform::Details::VectorProxy<T>` te iteratory `Platform::Details::ArrowProxy<T>` używają klas proxy i __\*__ __->__ zapewniają dostęp do poszczególnych elementów za pośrednictwem operatorów , i __ \[],__ zgodnie z wymaganiami biblioteki standardowej. Ściśle rzecz biorąc, `IVector<Person^> vec`biorąc pod `*begin(vec)` `VectorProxy<Person^>`uwagę , rodzaj jest . Jednak obiekt proxy jest prawie zawsze przezroczysty dla kodu. Te obiekty serwera proxy nie są udokumentowane, ponieważ są one tylko do użytku wewnętrznego przez iteratory, ale warto wiedzieć, jak działa mechanizm.

W przypadku `range for` korzystania `IVector` z pętli `auto&&` nad kontenerami, użyj, aby `VectorProxy` włączyć zmienną iteratora do powiązania poprawnie z elementami. Jeśli `auto` używasz `auto&`lub , ostrzeżenie kompilatora `VectoryProxy` C4239 jest wywoływana i jest wymieniony w tekście ostrzeżenia.

Na poniższej `range for` ilustracji `IVector<Person^>`przedstawiono pętlę nad . Należy zauważyć, że wykonanie jest zatrzymane w punkcie przerwania w wierszu 64. Okno **QuickWatch** pokazuje, że `p` zmienna iteratora `m_v` `m_i` `VectorProxy<Person^>` jest w rzeczywistości zmienne, które ma i element członkowski. Jednak po wywołaniu `GetType` tej zmiennej zwraca identyczny `Person` `p2`typ do wystąpienia . Na wynos jest `VectorProxy` `ArrowProxy` to, że chociaż i może pojawić się w **QuickWatch**, debuger niektórych błędów kompilatora lub innych miejscach, zazwyczaj nie trzeba jawnie kod dla nich.

![VectorProxy w zakresie&#45;oparty na pętli](../cppcx/media/vectorproxy-1.png "VectorProxy w zakresie&#45;oparty na pętli")

Jeden scenariusz, w którym trzeba kod wokół obiektu proxy `dynamic_cast` jest, gdy trzeba wykonać na elementy — na przykład, gdy `UIElement` szukasz obiektów XAML określonego typu w kolekcji elementu. W takim przypadku należy najpierw rzutować element na [platformę::Object](../cppcx/platform-object-class.md)^, a następnie wykonać rzut dynamiczny:

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

W tym przykładzie pokazano, jak wstawić elementy i wyszukać je w `Map` [platformie::Collections::Map](../cppcx/platform-collections-map-class.md), a następnie zwrócić jako tylko do odczytu [windows::Foundation::Collections::IMapView](/uwp/api/windows.foundation.collections.imapview-2) typu.

[!code-cpp[cx_collections#04](../cppcx/codesnippet/CPP/collections/class1.cpp#04)]

Ogólnie rzecz biorąc, w przypadku `std::map` funkcji mapy wewnętrznej preferuj typ ze względu na wydajność. Jeśli musisz przekazać kontener przez ABI, skonstruuj [platformę::Kolekcje::Map](../cppcx/platform-collections-map-class.md) z `Map` [std::map](../standard-library/map-class.md) i zwróć jako [windows::Foundation::Collections::IMap](/uwp/api/windows.foundation.collections.imap-2). Jeśli spróbujesz `Map` użyć typu w public return wartość lub parametr, błąd kompilatora C3986 zostanie podniesiona. Błąd można naprawić, zmieniając `Map` wartość `IMap`na . W niektórych przypadkach — na przykład, jeśli nie dokonujesz dużej liczby odnośnych lub wstawień, a często przekazujesz kolekcję przez ABI — używanie `Platform::Collections::Map` go od początku może być tańsze i uniknąć kosztów konwersji `std::map`. W każdym przypadku należy unikać wyszukiwania `IMap` i wstawiać operacje na, ponieważ są one najmniej wydajne z trzech typów. Konwertuj `IMap` tylko w punkcie, w który przekazujesz kontenera przez ABI.

## <a name="value-types-in-map"></a>Typy wartości na mapie

Elementy w [platformie::Kolekcje::Map](../cppcx/platform-collections-map-class.md) są uporządkowane. Każdy element, który `Map` ma być przechowywany w musi obsługiwać mniej niż porównanie ze ścisłą słabą kolejność, niejawnie lub przy użyciu niestandardowego [stl::less](../standard-library/less-struct.md) komparatora, który można podać. Typy skalarne obsługują porównanie niejawnie. W przypadku typów wartości innych `Windows::Foundation::DateTime`niż skalarne, takich `objA->UniqueID < objB->UniqueID`jak porównanie niestandardowe lub dla porównań niestandardowych, należy podać niestandardowy komparator.

## <a name="collection-types"></a>Typy kolekcji

Kolekcje dzielą się na cztery kategorie: modyfikowalne wersje i tylko do odczytu kolekcji sekwencji i kolekcji zespolonych. Ponadto C++/CX zwiększa kolekcje, zapewniając trzy klasy iteratora, które upraszczają dostęp do kolekcji.

Elementy kolekcji modyfikowalne można zmienić, ale elementy kolekcji tylko do odczytu, który jest znany jako *widok,* można odczytać tylko. Elementy [platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) lub[Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md) kolekcji można uzyskać za pomocą iteratora lub kolekcji [Vector::GetAt](../cppcx/platform-collections-vector-class.md#getat) i indeksu. Elementy kolekcji zespolona są dostępne za pomocą kolekcji [Map::Lookup](../cppcx/platform-collections-map-class.md#lookup) i klucza.

[Platform::Collections::Map, klasa](../cppcx/platform-collections-map-class.md)<br/>
Kolekcja modyfikowalna, zespolowalna. Elementy mapy są parami klucz-wartość. Wyszukiwanie klucza, aby pobrać jego skojarzoną wartość i iteracji za pośrednictwem wszystkich par klucza wartości, są obsługiwane.

`Map`i `MapView` są szablonami na `<K, V, C = std::less<K>>`; w związku z tym można dostosować komparatora.  Dodatkowo i `Vector` `VectorView` są szablony `<T, E = std::equal_to<T>>` na tak, że można `IndexOf()`dostosować zachowanie programu . Jest to ważne `Vector` głównie `VectorView` dla i struktury wartości. Na przykład, aby utworzyć\<Vector Windows::Foundation::DateTime>, należy podać niestandardowy komparator, ponieważ DateTime nie przeciąża == operatora.

[Platform::Collections::MapView, klasa](../cppcx/platform-collections-mapview-class.md)<br/>
Wersja tylko do odczytu `Map`.

[Platform::Collections::Vector, klasa](../cppcx/platform-collections-vector-class.md)<br/>
Kolekcja sekwencji modyfikowalne. `Vector<T>`obsługuje stały dostęp losowy i zamortyzowany czas operacji [dołączania..](../cppcx/platform-collections-vector-class.md#append)

[Platform::Collections::VectorView, klasa](../cppcx/platform-collections-vectorview-class.md)<br/>
Wersja tylko do odczytu `Vector`.

[Platform::Collections::InputIterator, klasa](../cppcx/platform-collections-inputiterator-class.md)<br/>
Iterator STL, który spełnia wymagania iteratora wejściowego STL.

[Platform::Collections::VectorIterator, klasa](../cppcx/platform-collections-vectoriterator-class.md)<br/>
Iterator STL, który spełnia wymagania iteratora modyfikowatego dostępu losowego STL.

[Platform::Collections::VectorViewIterator, klasa](../cppcx/platform-collections-vectorviewiterator-class.md)<br/>
Iterator STL, który spełnia wymagania iteratora `const` dostępu losowego STL.

### <a name="begin-and-end-functions"></a>begin() i end()

Aby uprościć użycie STL `VectorView` `Map`do `MapView`przetwarzania `Vector`, `Windows::Foundation::Collections` , , i dowolnych obiektów, C ++/CX obsługuje przeciążenia [funkcji funkcji i](../cppcx/begin-function.md) zakończenia [funkcji](../cppcx/end-function.md) niebędących elementami członkowskimi.

W poniższej tabeli wymieniono dostępne iteratory i funkcje.

|Iteratory|Funkcje|
|---------------|---------------|
|[Platforma::Kolekcje::VectorIterator\<T>](../cppcx/platform-collections-vectoriterator-class.md)<br /><br /> (Wewnętrznie przechowuje [system Windows::Foundation::Collections::\<IVector T>](/uwp/api/windows.foundation.collections.ivector-1) i int.)|[begin](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md)([Windows::Foundation::Collections::\<IVector T>](/uwp/api/windows.foundation.collections.ivector-1))|
|[Platforma::Kolekcje::VectorViewIterator\<T>](../cppcx/platform-collections-vectorviewiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [\<IVectorView T>](/uwp/api/windows.foundation.collections.ivectorview-1)^ i int.)|[begin](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) ([\<IVectorView T>](/uwp/api/windows.foundation.collections.ivectorview-1)^)|
|[Platforma::Kolekcje::InputIterator\<T>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IIterator\<T>](/uwp/api/windows.foundation.collections.iiterator-1)^ i T.)|[begin](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) [\<(IIterable T>](/uwp/api/windows.foundation.collections.iiterable-1))|
|[Platforma::Kolekcje::InputIterator<IKeyValuePair\<K, V>^>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IIterator\<T>](/uwp/api/windows.foundation.collections.iiterator-1)^ i T.)|[begin](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) ([IMap\<K,V>](/uwp/api/windows.foundation.collections.imap-2).|
|[Platforma::Kolekcje::InputIterator<IKeyValuePair\<K, V>^>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IIterator\<T>](/uwp/api/windows.foundation.collections.iiterator-1)^ i T.)|[begin](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) ([Windows::Foundation::Collections::IMapView](/uwp/api/windows.foundation.collections.imapview-2))|

### <a name="collection-change-events"></a>Zdarzenia zmiany kolekcji

`Vector`i `Map` obsługuje powiązania danych w kolekcjach XAML przez implementowanie zdarzeń, które występują, gdy obiekt kolekcji zostanie zmieniony lub zresetowany lub gdy dowolny element kolekcji zostanie wstawiony, usunięty lub zmieniony. Można napisać własne typy, które obsługują databinding, chociaż nie można dziedziczyć z `Map` lub `Vector` ponieważ te typy są zapieczętowane.

Delegaty [Windows::Foundation::Collections::VectorChangedEventHandler](/uwp/api/windows.foundation.collections.vectorchangedeventhandler-1) i [Windows::Foundation::Collections::MapChangedEventHandler](/uwp/api/windows.foundation.collections.mapchangedeventhandler-2) delegują określanie podpisów dla programów obsługi zdarzeń dla zdarzeń zmiany kolekcji. [Windows::Foundation::Collections::CollectionChange](/uwp/api/windows.foundation.collections.collectionchange) public enum class `Platform::Collection::Details::MapChangedEventArgs` `Platform::Collections::Details::VectorChangedEventArgs` i ref klasy, przechowywać argumenty zdarzenia, aby ustalić, co spowodowało zdarzenie. Typy `*EventArgs` są zdefiniowane w obszarze `Details` nazw, ponieważ nie trzeba ich konstruować ani używać jawnie podczas używania `Map` lub `Vector`.

## <a name="see-also"></a>Zobacz też

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Odwołanie do języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
