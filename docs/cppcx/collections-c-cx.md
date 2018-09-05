---
title: Kolekcje (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 914da30b-aac5-4cd7-9da3-a5ac08cdd72c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0be29ed74b2c5abf8bc3c781900caa61ada3713f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693081"
---
# <a name="collections-ccx"></a>Kolekcje (C + +/ CX)
W języku C + +/ CX programu, aby włączyć bezpłatne korzystanie z kontenerów standardowy szablon biblioteki (STL) lub dowolny inny typ zdefiniowany przez użytkownika kolekcji. Jednak gdy przekazujesz kolekcji i z powrotem między interfejsem binarnym aplikacji (ABI) środowiska uruchomieniowego Windows — na przykład, kontrolki XAML lub klienta JavaScript — należy użyć typów kolekcji środowiska wykonawczego Windows.  
  
 Środowisko wykonawcze Windows definiuje interfejsach dla kolekcji powiązanych typów i C + +/ CX zapewnia konkretnych implementacji C++ w pliku nagłówkowym collection.h. Ta ilustracja przedstawia relacje między tymi typami kolekcji:  
  
 ![C&#43;&#43;&#47;CX drzewo dziedziczenia dla typów kolekcji](../cppcx/media/cppcxcollectionsinheritancetree.png "CPPCXCollectionsInheritanceTree")  
  
-   [Platform::Collections:: Vector, klasa](../cppcx/platform-collections-vector-class.md) przypomina [klasy std::vector](../standard-library/vector-class.md).  
  
-   [Platform::Collections:: map, klasa](../cppcx/platform-collections-map-class.md) klasa przypomina [klasy std::map](../standard-library/map-class.md).  
  
-   [Platform::Collections:: vectorview, klasa](../cppcx/platform-collections-vectorview-class.md) i[platform::Collections:: mapview, klasa](../cppcx/platform-collections-mapview-class.md) wersji tylko do odczytu `Vector` i `Map`.  
  
-   Iteratory są zdefiniowane w [Namespace Platform::Collections](../cppcx/platform-collections-namespace.md). Te Iteratory spełniają wymagania dla iteratorów STL i umożliwiają użycie [std::find](../standard-library/algorithm-functions.md#find), [std::count_if](../standard-library/algorithm-functions.md#count_if)i inne algorytmy STL, na dowolnym [Windows::Foundation:: Collections](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.aspx) typ interfejsu lub [Platform::Collections](../cppcx/platform-collections-namespace.md) konkretne typu. Na przykład oznacza to, że można wykonać iterację kolekcji w składnik środowiska wykonawczego Windows, który jest tworzony w języku C# i dotyczą algorytmem STL.  
  
    > [!IMPORTANT]
    >  Serwer proxy Iteratory `VectorIterator` i `VectorViewIterator` korzystanie z obiektów pośredniczących `VectoryProxy<T>` i `ArrowProxy<T>` użycia za pomocą kontenerów STL. Aby uzyskać więcej informacji zobacz "VectorProxy elements" w dalszej części tego artykułu.  
  
-   C + +/ CX kolekcji typów bezpieczeństwo wątków w tej samej gwarantuje, że obsługuje kontenery STL pomocy technicznej.  
  
-   [Windows::Foundation::Collections::IObservableVector](/uwp/api/Windows.Foundation.Collections.IObservableVector_T_) i [Windows::Foundation::Collections::IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) zdefiniowania zdarzeń, które są wywoływane, gdy zmienia się kolekcja na różne sposoby. Wdrażając te interfejsy [platform::Collections:: map](../cppcx/platform-collections-map-class.md) i [platform::Collections:: Vector](../cppcx/platform-collections-vector-class.md) obsługuje powiązanie danych z kolekcjami XAML. Na przykład, jeśli masz `Vector` , jest powiązany z danymi `Grid`, kiedy należy dodać element do kolekcji, zmiany są widoczne w Interfejsie użytkownika siatki.  
  
## <a name="vector-usage"></a>Użycie wektora  
 Jeśli klasa ma do przekazania kontenerem sekwencyjnym do innego składnika środowiska wykonawczego Windows, użyj [Windows::Foundation:: Collections:: IVector\<T >](https://msdn.microsoft.com/library/windows/apps/br206631.aspx) jako parametr lub zwracany typ i [platformy:: Collections::Vector\<T >](../cppcx/platform-collections-vector-class.md) jako konkretną implementację. Jeśli spróbujesz użyć `Vector` typu w publicznych wartość zwracana lub parametr, błąd kompilatora C3986 zostanie wygenerowany. Można naprawić błąd, zmieniając `Vector` do `IVector`.  
  
> [!IMPORTANT]
>  Jeśli przekazujesz sekwencję w ramach własnego programu, należy użyć albo `Vector` lub `std::vector` ponieważ są one bardziej wydajne niż `IVector`. Użyj `IVector` tylko gdy przekazujesz kontenera między interfejsem ABI.  
>   
>  System typów środowiska wykonawczego Windows nie obsługuje pojęcie Tablice nieregularne i dlatego nie można przekazać IVector < Platform::Array\<T >> jako parametr zwracany wartość lub metody. Aby przekazać tablicę nieregularną lub sekwencji między interfejsem ABI, należy użyć `IVector<IVector<T>^>`.  
  
 `Vector<T>` udostępnia metody, które są wymagane w przypadku dodawania, usuwania i uzyskiwania dostępu do elementów w kolekcji i jest niejawnie konwertowany na `IVector<T>`. Można również użyć algorytmów STL w wystąpieniach tej `Vector<T>`. W poniższym przykładzie pokazano niektóre podstawowe użycia. [Begin, funkcja](../cppcx/begin-function.md) i [end, funkcja](../cppcx/end-function.md) poniżej pochodzą z `Platform::Collections` przestrzeni nazw, nie `std` przestrzeni nazw.  
  
 [!code-cpp[cx_collections#01](../cppcx/codesnippet/CPP/collections/class1.cpp#01)]  
  
 Jeśli masz istniejący kod, który używa `std::vector` i chcesz użyć go ponownie w składnika wykonawczego Windows, po prostu użyj jednej z `Vector` konstruktorów, które przyjmuje `std::vector` lub para iteratorów do konstruowania `Vector` w punkcie, w którym należy przekazać Kolekcja między interfejsem ABI. Poniższy przykład pokazuje, jak używać `Vector` przenoszenie konstruktora by go zainicjalizować wydajne z `std::vector`. Po zakończeniu operacji przenoszenia, oryginalnym `vec` zmienna nie jest już prawidłowy.  
  
 [!code-cpp[cx_collections#02](../cppcx/codesnippet/CPP/collections/class1.cpp#02)]  
  
 Jeśli masz wektor ciągów, które muszą upłynąć między ABI w pewnym momencie w przyszłości, należy zdecydować, czy do tworzenia ciągów początkowo jako `std::wstring` typów lub jako `Platform::String^` typów. Jeśli masz dużo przetwarzania na ciągi, należy użyć `wstring`. W przeciwnym razie Tworzenie ciągów jako `Platform::String^` typów i uniknąć kosztów konwertowania go później. Należy również określić, czy umieścić te ciągi do `std:vector` lub `Platform::Collections::Vector` wewnętrznie. Ogólną praktyką jest, należy użyć `std::vector` , a następnie utwórz `Platform::Vector` od niego tylko wtedy, gdy kontener jest przekazywane między interfejsem ABI.  
  
## <a name="value-types-in-vector"></a>Typy wartości w wektorze  
 Każdy element ma być przechowywany w [platform::Collections:: Vector](../cppcx/platform-collections-vector-class.md) musi obsługiwać porównanie równości, niejawnie lub przy użyciu niestandardowego [std::equal_to](../standard-library/equal-to-struct.md) komparator przez Ciebie. Wszystkie typy odwołań i wszystkie typy skalarne, niejawnie obsługuje porównywanie równości. Dla nieskalarnego typy wartości takie jak [Windows::Foundation::DateTime](https://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx), lub niestandardowych porównania — na przykład `objA->UniqueID == objB->UniqueID`— należy podać obiekt funkcję niestandardową.  
   
  
## <a name="vectorproxy-elements"></a>Elementy VectorProxy  
 [Platform::Collections:: vectoriterator](../cppcx/platform-collections-vectoriterator-class.md) i [platform::Collections:: vectorviewiterator](../cppcx/platform-collections-vectorviewiterator-class.md) korzystanie z `range for` pętli i algorytmy, takie jak [std::sort](../standard-library/algorithm-functions.md#sort) z [ IVector\<T >](https://msdn.microsoft.com/library/windows/apps/br206631.aspx) kontenera. Ale `IVector` elementy nie są dostępne za pośrednictwem C++ wyłuskanie wskaźnika; są one dostępne tylko za pośrednictwem [GetAt](https://msdn.microsoft.com/library/windows/apps/br206634.aspx) i [SetAt](https://msdn.microsoft.com/library/windows/apps/br206642.aspx) metody. Dlatego te Iteratory używać klasy serwera proxy `Platform::Details::VectorProxy<T>` i `Platform::Details::ArrowProxy<T>` zapewniać dostęp do poszczególnych elementów za pomocą `*`, `->`, i `[]` operatorów, zgodnie z wymogami STL. Ściśle rzecz ujmując, biorąc pod uwagę `IVector<Person^> vec`, typ `*begin(vec)` jest `VectorProxy<Person^>`. Obiekt serwera proxy jest jednak prawie zawsze przejrzyste w kodzie. Te obiekty serwera proxy nie zostały zamieszczone, ponieważ są one tylko do użytku wewnętrznego przez Iteratory, ale warto wiedzieć, jak działa mechanizm.  
  
 Kiedy używasz `range for` pętli `IVector` kontenery, użyj `auto&&` umożliwiające zmienna iteratora, do powiązania poprawnie do `VectorProxy` elementów. Jeśli używasz `auto` lub `auto&`, ostrzeżenia kompilatora, które jest wywoływane C4239 i `VectoryProxy` jest wymieniony w tekst ostrzeżenia.  
  
 Poniższa ilustracja przedstawia `range for` pętli `IVector<Person^>`. Należy zauważyć, że wykonanie zostanie zatrzymana w punkt przerwania w wierszu 64. **QuickWatch** okno pokazuje, że zmienna sterująca `p` jest w rzeczywistości `VectorProxy<Person^>` zawierający `m_v` i `m_i` zmiennych Członkowskich. Jednak jeśli wywołasz `GetType` w tej zmiennej zwraca typ identyczne `Person` wystąpienia `p2`. Wnioskiem jest to, że chociaż `VectorProxy` i `ArrowProxy` może się pojawić **QuickWatch**, debuger niektórych błędów kompilatora lub z innych miejsc, zwykle nie trzeba jawnie kodu dla nich.  
  
 ![VectorProxy w zakresie&#45;na podstawie pętli for](../cppcx/media/vectorproxy-1.png "VectorProxy_1")  
  
 Jeden scenariusz, w którym zostały do kodu wokół obiektu serwera proxy jest, gdy trzeba wykonać `dynamic_cast` od elementów — na przykład podczas szukania dla obiektów określonego typu w XAML `UIElement` kolekcji elementów. W takim przypadku należy najpierw rzutować elementu [Platform::Object](../cppcx/platform-object-class.md)^, a następnie wykonaj rzutowanie dynamicznych:  
  
```  
  
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
 W tym przykładzie pokazano, jak wstawić elementów i wyszukiwać [platform::Collections:: map](../cppcx/platform-collections-map-class.md), a następnie zwracają `Map` jako tylko do odczytu [Windows::Foundation::Collections::IMapView] / platformy uniwersalnej systemu Windows/api / Typ Windows.Foundation.Collections.IMapView_K_V_).  
  
 [!code-cpp[cx_collections#04](../cppcx/codesnippet/CPP/collections/class1.cpp#04)]  
  
 Ogólnie rzecz biorąc, funkcji wewnętrznych mapy Preferuj `std::map` typu, ze względu na wydajność. Jeśli trzeba przekazać kontenera między interfejsem ABI skonstruować [platform::Collections:: map](../cppcx/platform-collections-map-class.md) z [std::map](../standard-library/map-class.md) i zwracają `Map` jako [Windows::Foundation:: Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_). Jeśli spróbujesz użyć `Map` typu w publicznych wartość zwracana lub parametr, błąd kompilatora C3986 zostanie wygenerowany. Można naprawić błąd, zmieniając `Map` do `IMap`. W niektórych przypadkach — na przykład, jeśli nie wykonujesz dużą liczbę wyszukiwań lub wstawienia i są przekazywanie kolekcji między interfejsem ABI często — może być mniej kosztowne użyć `Platform::Collections::Map` od samego początku i uniknąć kosztów konwertowania `std::map`. W każdym przypadku należy unikać wyszukiwania i operacje wstawiania na `IMap` ponieważ są one co najmniej wydajne z trzech typów. Konwertuj na `IMap` tylko w punkcie przekazać kontenera między interfejsem ABI.  
  
## <a name="value-types-in-map"></a>Typy wartości na mapie  
 Elementy w [platform::Collections:: map](../cppcx/platform-collections-map-class.md) są uporządkowane. Każdy element ma być przechowywany w `Map` musi obsługiwać mniej-niż porównania z ścisłym słabym porządkowaniem, niejawnie lub przy użyciu niestandardowego [stl::less](../standard-library/less-struct.md) komparator przez Ciebie. Typy skalarne, które niejawnie obsługuje porównania. Dla nieskalarnego typy wartości takie jak `Windows::Foundation::DateTime`, lub niestandardowych porównania — na przykład `objA->UniqueID < objB->UniqueID`— musisz podać niestandardowy komparator.  
  
## <a name="collection-types"></a>Typy kolekcji  
 Kolekcje można podzielić na cztery kategorie: wersje można modyfikować i tylko do odczytu programu sekwencji kolekcji i kolekcji asocjacyjnych. Ponadto, C + +/ CX zwiększa kolekcje, zapewniając trzy klasy iteratora, które ułatwiają uzyskiwanie dostępu do kolekcji. 
  
 Można zmienić elementy kolekcji można modyfikować, ale elementów kolekcji tylko do odczytu, który jest znany jako *widoku*, mogą być odczytane tylko. Elementy [platform::Collections:: Vector](../cppcx/platform-collections-vector-class.md) lub[platform::Collections:: vectorview](../cppcx/platform-collections-vectorview-class.md) kolekcji jest możliwy za pomocą iteratora lub kolekcji [Vector::GetAt](../cppcx/platform-collections-vector-class.md#getat) i indeksu. Elementy kolekcji asocjacyjnych jest możliwy za pomocą kolekcji [Map::Lookup](../cppcx/platform-collections-map-class.md#lookup) , jak i klucz.  
  
 [Platform::Collections::Map, klasa](../cppcx/platform-collections-map-class.md)  
 Można modyfikować asocjacyjnych kolekcji. Elementy mapy są pary klucz wartość. Wyszukiwanie klucza można pobrać jej powiązaną wartość i przechodzenie przez wszystkie pary klucz wartość, są obsługiwane.  
  
 `Map` i `MapView` są oparte na szablonach na `<K, V, C = std::less<K>>`; w związku z tym, można dostosować komparator.  Ponadto `Vector` i `VectorView` są oparte na szablonach na `<T, E = std::equal_to<T>>` tak, aby dostosować zachowanie `IndexOf()`. Jest to ważne głównie na potrzeby `Vector` i `VectorView` struktur wartość. Na przykład, aby utworzyć wektor\<Windows::Foundation::DateTime >, należy podać niestandardowy komparator, ponieważ daty i godziny nie przeciążać == — operator.  
  
 [Platform::Collections::MapView, klasa](../cppcx/platform-collections-mapview-class.md)  
 Tylko do odczytu wersję `Map`.  
  
 [Platform::Collections::Vector, klasa](../cppcx/platform-collections-vector-class.md)  
 Kolekcja sekwencji można modyfikować. `Vector<T>` obsługuje stałą czasu dostępu losowego i amortyzowanego stała w czasie [Append](../cppcx/platform-collections-vector-class.md#append) operacji...  
  
 [Platform::Collections::VectorView, klasa](../cppcx/platform-collections-vectorview-class.md)  
 Tylko do odczytu wersję `Vector`.  
  
 [Platform::Collections::InputIterator, klasa](../cppcx/platform-collections-inputiterator-class.md)  
 Iterator STL, który spełnia wymagania iteratora danych wejściowych w STL.  
  
 [Platform::Collections::VectorIterator, klasa](../cppcx/platform-collections-vectoriterator-class.md)  
 Iterator STL, który spełnia wymagania iteratora dostępu swobodnego mutable w STL.  
  
 [Platform::Collections::VectorViewIterator, klasa](../cppcx/platform-collections-vectorviewiterator-class.md)  
 Iterator STL, który spełnia wymagania STL `const` iteratora dostępu swobodnego.  
  
### <a name="begin-and-end-functions"></a>Funkcje BEGIN() i metodę end()  
 Ułatwiają korzystanie z biblioteki STL, aby przetworzyć `Vector`, `VectorView`, `Map`, `MapView`i dowolnego `Windows::Foundation::Collections` obiektów, w języku C + +/ CX obsługuje przeciążenia [begin, funkcja](../cppcx/begin-function.md) i [zakończenia Funkcja](../cppcx/end-function.md) funkcje nieczłonkowskie.  
  
 W poniższej tabeli wymieniono dostępne Iteratory i funkcje.  
  
|Iteratory|Funkcje|  
|---------------|---------------|  
|[Platform::Collections:: vectoriterator\<T >](../cppcx/platform-collections-vectoriterator-class.md)<br /><br /> (Wewnętrznie przechowuje [Windows::Foundation:: Collections:: IVector\<T >](https://msdn.microsoft.com/library/windows/apps/br206631.aspx) i int.)|[Rozpocznij](../cppcx/begin-function.md)/ [zakończenia](../cppcx/end-function.md)([Windows::Foundation:: Collections:: IVector\<T >](https://msdn.microsoft.com/library/windows/apps/br206631.aspx))|  
|[Platform::Collections:: vectorviewiterator\<T >](../cppcx/platform-collections-vectorviewiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IVectorView\<T >](https://msdn.microsoft.com/library/windows/apps/br226058.aspx)^ i int.)|[Rozpocznij](../cppcx/begin-function.md)/ [zakończenia](../cppcx/end-function.md) ([IVectorView\<T >](https://msdn.microsoft.com/library/windows/apps/br226058.aspx)^)|  
|[Platform::Collections:: inputiterator\<T >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IIterator\<T >](https://msdn.microsoft.com/library/windows/apps/br226026.aspx)^ i T.)|[Rozpocznij](../cppcx/begin-function.md)/ [zakończenia](../cppcx/end-function.md) ([IIterable\<T >](https://msdn.microsoft.com/library/windows/apps/br226024.aspx))|  
|[Platform::Collections:: inputiterator < IKeyValuePair\<K, V > ^ >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IIterator\<T >](https://msdn.microsoft.com/library/windows/apps/br226026.aspx)^ i T.)|[Rozpocznij](../cppcx/begin-function.md)/ [zakończenia](../cppcx/end-function.md) ([IMap\<K, V >](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).|  
|[Platform::Collections:: inputiterator < IKeyValuePair\<K, V > ^ >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IIterator\<T >](https://msdn.microsoft.com/library/windows/apps/br226026.aspx)^ i T.)|[Rozpocznij](../cppcx/begin-function.md)/ [zakończenia](../cppcx/end-function.md) ([Windows:: Foundation::Collections::IMapView]/uwp/api/Windows.Foundation.Collections.IMapView_K_V_))|  
  
### <a name="collection-change-events"></a>Zbieranie zdarzeń zmiany  
 `Vector` i `Map` obsługuje wiązania danych w kolekcjach XAML poprzez implementację zdarzenia występujące po zmianie obiektu kolekcji lub zresetować lub po wstawieniu dowolnego elementu w kolekcji, usunięte lub zmienione. Można napisać własne typy tego wiązania danych pomocy technicznej, mimo że nie może dziedziczyć z `Map` lub `Vector` ponieważ te typy są zamknięte.  
  
 [Windows::Foundation::Collections::VectorChangedEventHandler](/uwp/api/windows.foundation.collections.vectorchangedeventhandler) i [Windows::Foundation::Collections::MapChangedEventHandler](/uwp/api/windows.foundation.collections.mapchangedeventhandler) delegatów Określ podpisów dla obsługi zdarzeń zbieranie zdarzeń zmiany. [Windows::Foundation::Collections::CollectionChange](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx) klasy publicznym typie wyliczeniowym i `Platform::Collection::Details::MapChangedEventArgs` i `Platform::Collections::Details::VectorChangedEventArgs` klasy ref przechowywania argumenty zdarzeń, aby ustalić, który spowodował zdarzenie. *`EventArgs` Typy są definiowane w `Details` przestrzeni nazw, ponieważ nie trzeba konstrukcja lub używać ich jawnie, gdy używasz `Map` lub `Vector`.  
  
## <a name="see-also"></a>Zobacz też  
 [System typów](../cppcx/type-system-c-cx.md)   
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)