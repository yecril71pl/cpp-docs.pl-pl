---
title: Kolekcje (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 914da30b-aac5-4cd7-9da3-a5ac08cdd72c
caps.latest.revision: "35"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5c97a264488e8b382091b24cdef8faae4c7bbfc0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="collections-ccx"></a>Kolekcje (C + +/ CX)
W języku C + +/ CX programu, możesz wprowadzić wolnego korzystanie z kontenerów standardowa biblioteka szablonów (STL) lub dowolnego typu kolekcja zdefiniowanych przez użytkownika. Jednak gdy przekazujesz kolekcji i z powrotem przez interfejs binarne (ABI) środowiska wykonawczego systemu Windows — na przykład do formantu XAML lub klientowi JavaScript — należy użyć typów kolekcji środowiska wykonawczego systemu Windows.  
  
 Środowisko wykonawcze systemu Windows definiuje interfejsach dla kolekcji i powiązanych typów i C + +/ CX udostępnia konkretną implementacje C++ w pliku nagłówka collection.h. Ta ilustracja prezentuje jedynie relacje między typami kolekcji:  
  
 ![C &43; &#43; &#47; CX drzewa dziedziczenia dla typów kolekcji](../cppcx/media/cppcxcollectionsinheritancetree.png "CPPCXCollectionsInheritanceTree")  
  
-   [Klasy Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) podobny [std::vector klasy](../standard-library/vector-class.md).  
  
-   [Klasy Platform::Collections::Map](../cppcx/platform-collections-map-class.md) podobny klasy [std::map klasy](../standard-library/map-class.md).  
  
-   [Klasa platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md) i[klasy Platform::Collections::MapView](../cppcx/platform-collections-mapview-class.md) wersji tylko do odczytu `Vector` i `Map`.  
  
-   Iteratory są zdefiniowane w [Namespace Platform::Collections](../cppcx/platform-collections-namespace.md). Te Iteratory spełniają wymagania dotyczące Iteratory STL i korzystanie z [std::find](../standard-library/algorithm-functions.md#find), [std::count_if](../standard-library/algorithm-functions.md#count_if)oraz innym algorytmom STL na dowolnym [Windows::Foundation::Collections](http://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.aspx) typ interfejsu lub [Platform::Collections](../cppcx/platform-collections-namespace.md) specyficzne typu. Na przykład oznacza to, czy można wykonać iterację kolekcji w składnika środowiska wykonawczego systemu Windows, który jest tworzony w języku C# i dotyczą algorytm STL.  
  
    > [!IMPORTANT]
    >  Iteratory proxy `VectorIterator` i `VectorViewIterator` korzystanie z obiektów pośredniczących `VectoryProxy<T>` i `ArrowProxy<T>` umożliwienie użycia za pomocą kontenery STL. Aby uzyskać więcej informacji zobacz "VectorProxy elementy" w dalszej części tego artykułu.  
  
-   C + +/ CX kolekcji typów tego samego bezpieczeństwo wątków gwarantuje, że obsługuje kontenery STL pomocy technicznej.  
  
-   [Windows::Foundation::Collections::IObservableVector](http://msdn.microsoft.com/library/windows/apps/br226052.aspx) i [Windows::Foundation::Collections::IObservableMap](http://msdn.microsoft.com/library/windows/apps/br226050.aspx) definiowanie zdarzeń, które są uruchamiane, gdy zmienia się kolekcja na różne sposoby. Wdrażając te interfejsy [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) i [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) obsługuje wiązania danych z kolekcjami XAML. Na przykład, jeśli masz `Vector` który jest powiązany z danymi `Grid`, kiedy należy dodać element do kolekcji, znajduje odzwierciedlenie w Interfejsie użytkownika siatki.  
  
## <a name="vector-usage"></a>Użycie wektora  
 Jeśli klasy do przekazania kontenera sekwencji do innego składnika środowiska wykonawczego systemu Windows, użyj [Windows::Foundation::Collections:: IVector\<T >](http://msdn.microsoft.com/library/windows/apps/br206631.aspx) jako parametr lub typ zwracany i [platformy:: Collections::Vector\<T >](../cppcx/platform-collections-vector-class.md) jako konkretną implementację. Jeśli próba użycia `Vector` typu publicznego zwracana wartość lub parametr C3986 zostanie wygenerowany błąd kompilatora. Naprawić ten błąd, zmieniając `Vector` do `IVector`.  
  
> [!IMPORTANT]
>  Jeśli sekwencja jest przekazywany w aplikacji użytkownika, należy użyć albo `Vector` lub `std::vector` ponieważ są one bardziej wydajne niż `IVector`. Użyj `IVector` tylko gdy przekazujesz kontenera między interfejsem ABI.  
>   
>  System typów środowiska wykonawczego systemu Windows nie obsługuje pojęcia Tablice nieregularne i dlatego nie można przekazać IVector < Platform::Array\<T >> jako parametr zwrotnego wartość lub metody. Aby przekazać tablicy nieregularnej lub sekwencję sekwencji między interfejsem ABI, należy użyć `IVector<IVector<T>^>`.  
  
 `Vector<T>`udostępnia metody, które są wymagane, dodawanie, usuwanie i uzyskiwanie dostępu do elementów w kolekcji i jest niejawnie przekonwertować `IVector<T>`. Umożliwia także algorytmów STL w wystąpieniach `Vector<T>`. W poniższym przykładzie pokazano niektóre podstawowe sposoby użycia. [Rozpocząć funkcja](../cppcx/begin-function.md) i [kończyć funkcja](../cppcx/end-function.md) Oto z `Platform::Collections` przestrzeni nazw nie `std` przestrzeni nazw.  
  
 [!code-cpp[cx_collections#01](../cppcx/codesnippet/CPP/collections/class1.cpp#01)]  
  
 Jeśli masz istniejący kod, który używa `std::vector` i chcesz użyć go ponownie w składnika środowiska wykonawczego systemu Windows, wystarczy użyć jednego z `Vector` konstruktorów `std::vector` dysków lub para Iteratory do skonstruowania `Vector` w momencie, gdy przekazujesz Kolekcja między interfejsem ABI. Poniższy przykład przedstawia użycie `Vector` przenoszenie konstruktora dla inicjowania wydajne z `std::vector`. Po zakończeniu operacji przenoszenia oryginalnej `vec` zmienna nie jest już prawidłowy.  
  
 [!code-cpp[cx_collections#02](../cppcx/codesnippet/CPP/collections/class1.cpp#02)]  
  
 Jeśli masz wektor ciągów, które muszą upłynąć między ABI w pewnym momencie w przyszłości, należy określić, czy można utworzyć ciągów początkowo jako `std::wstring` typów lub jako `Platform::String^` typów. Jeśli masz dużo przetwarzania na ciągi, użyj `wstring`. W przeciwnym razie utwórz ciągi jako `Platform::String^` typów i uniknąć kosztów konwertowanie je później. Należy również określić, czy umieścić te ciągi do `std:vector` lub `Platform::Collections::Vector` wewnętrznie. Zalecanym rozwiązaniem, użyj `std::vector` , a następnie utworzyć `Platform::Vector` od niego tylko wtedy, gdy przekazujesz kontenera między interfejsem ABI.  
  
## <a name="value-types-in-vector"></a>Typy wartości w przypadku wektora  
 Dowolny element, aby były przechowywane w [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) musi obsługiwać porównania równości niejawnie lub przy użyciu niestandardowego [std::equal_to](../standard-library/equal-to-struct.md) komparatora podane. Wszystkie typy referencyjne i wszystkie typy skalarne niejawnie obsługuje porównywanie równości. Dla nieskalarnego typów wartości takich jak [Windows::Foundation::DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx), lub dla niestandardowych porównań — na przykład `objA->UniqueID == objB->UniqueID`— musisz podać obiektem funkcji niestandardowych.  
   
  
## <a name="vectorproxy-elements"></a>Elementy VectorProxy  
 [Platform::Collections::VectorIterator](../cppcx/platform-collections-vectoriterator-class.md) i [Platform::Collections::VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md) korzystanie z `range for` pętli i algorytmów, takich jak [std::sort](../standard-library/algorithm-functions.md#sort) z [IVector\<T >](http://msdn.microsoft.com/en-us/library/windows/apps/br206631.aspx) kontenera. Ale `IVector` elementy nie będą dostępne za pośrednictwem C++ wyłuskania wskaźnika; są one dostępne tylko za pomocą [GetAt](http://msdn.microsoft.com/library/windows/apps/br206634.aspx) i [SetAt](http://msdn.microsoft.com/library/windows/apps/br206642.aspx) metody. W związku z tym te Iteratory Użyj klasy serwera proxy `Platform::Details::VectorProxy<T>` i `Platform::Details::ArrowProxy<T>` umożliwia dostęp do poszczególnych elementów przy użyciu `*`, `->`, i `[]` operatorów, co jest wymagane przez STL. Mówiąc ściślej, podane `IVector<Person^> vec`, typ `*begin(vec)` jest `VectorProxy<Person^>`. Jednak obiekt serwera proxy prawie zawsze jest niewidoczny w kodzie. Te obiekty serwera proxy nie są udokumentowane, ponieważ są one tylko do użytku wewnętrznego przez Iteratory, ale warto wiedzieć, jak działa mechanizm.  
  
 Jeśli używasz `range for` pętli `IVector` kontenery, użyj `auto&&` umożliwiające zmienna sterująca powiązać poprawnie do `VectorProxy` elementów. Jeśli używasz `auto` lub `auto&`, ostrzeżenie kompilatora powstaje C4239 i `VectoryProxy` jest wymieniony w tekst ostrzeżenia.  
  
 Na poniższej ilustracji pokazano `range for` pętli `IVector<Person^>`. Należy zauważyć, że wykonanie jest zatrzymana na punkt przerwania w wierszu 64. **QuickWatch** okna wskazuje, że zmienna sterująca `p` jest w rzeczywistości `VectorProxy<Person^>` mający `m_v` i `m_i` zmiennych Członkowskich. Jednak jeśli wywołasz `GetType` w tej zmiennej zwraca typ identyczne do `Person` wystąpienia `p2`. Takeaway jest to, że chociaż `VectorProxy` i `ArrowProxy` może się pojawić **QuickWatch**, debuger niektóre błędy kompilatora lub innych miejscach, zwykle nie trzeba jawnie kodu dla nich.  
  
 ![VectorProxy w &#45; zakresu na podstawie pętli for](../cppcx/media/vectorproxy-1.png "VectorProxy_1")  
  
 Jest jednym ze scenariuszy masz kod wokół obiekt serwera proxy, gdy należy wykonać `dynamic_cast` dla elementów — na przykład podczas szukania dla obiektów określonego typu w XAML `UIElement` kolekcji elementów. W takim przypadku należy najpierw rzutować elementu [Platform::Object](../cppcx/platform-object-class.md)^, a następnie wykonać rzutowania dynamicznego:  
  
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
 W tym przykładzie pokazano, jak wstawić elementów i wyszukiwanie [Platform::Collections::Map](../cppcx/platform-collections-map-class.md), a następnie wróć `Map` jako tylko do odczytu [Windows::Foundation::Collections::IMapView](http://msdn.microsoft.com/library/windows/apps/br226037.aspx) typu.  
  
 [!code-cpp[cx_collections#04](../cppcx/codesnippet/CPP/collections/class1.cpp#04)]  
  
 Ogólnie rzecz biorąc, mapy wewnętrznej funkcji, należy wybrać `std::map` typu ze względu na wydajność. Jeśli trzeba przekazać kontenera między interfejsem ABI, skonstruować [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) z [std::map](../standard-library/map-class.md) i zwracać `Map` jako [Windows::Foundation —:: Collections::IMap](http://msdn.microsoft.com/library/windows/apps/br226042.aspx). Jeśli próba użycia `Map` typu publicznego zwracana wartość lub parametr C3986 zostanie wygenerowany błąd kompilatora. Naprawić ten błąd, zmieniając `Map` do `IMap`. W niektórych przypadkach — na przykład, jeśli nie utworzysz dużą liczbę wyszukiwań lub wstawienia i kolekcji są przekazywanie często między interfejsem ABI — może być mniej kosztowne użyć `Platform::Collections::Map` od początku i uniknąć kosztów konwertowanie `std::map`. W każdym przypadku uniknąć wyszukiwania i liczba operacji wstawienia na `IMap` ponieważ są to wydajność co najmniej trzech typów. Konwertuj na `IMap` tylko w punkcie przekazać kontenera między interfejsem ABI.  
  
## <a name="value-types-in-map"></a>Typy wartości w tablicy  
 Elementy w [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) są uporządkowane. Dowolny element, aby były przechowywane w `Map` musi obsługiwać mniej-niż porównanie z ograniczeniami niska porządkowanie niejawnie lub przy użyciu niestandardowego [stl::less](../standard-library/less-struct.md) komparatora podane. Typy skalarne niejawnie obsługuje porównania. Dla nieskalarnego typów wartości takich jak `Windows::Foundation::DateTime`, lub dla niestandardowych porównań — na przykład `objA->UniqueID < objB->UniqueID`— musisz podać komparatora niestandardowych.  
  
## <a name="collection-types"></a>Typy kolekcji  
 Kolekcje można podzielić na cztery kategorie: wersje można modyfikować i tylko do odczytu kolekcji sekwencji i asocjacyjnej kolekcji. Ponadto C + +/ CX zwiększa kolekcje, zapewniając trzech klas iteratora, które ułatwiają uzyskiwanie dostępu do kolekcji. 
  
 Elementy można modyfikować kolekcji można zmienić, ale elementów kolekcji tylko do odczytu, znany jako *widoku*, mogą być odczytywane tylko. Elementy [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) lub[Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md) kolekcji jest możliwy za pomocą iteratora lub kolekcji [Vector::GetAt](../cppcx/platform-collections-vector-class.md#getat) i indeksu. Elementy kolekcji asocjacyjnej jest możliwy za pomocą kolekcji [Map::Lookup](../cppcx/platform-collections-map-class.md#lookup) i klucza.  
  
 [Platform::Collections::Map, klasa](../cppcx/platform-collections-map-class.md)  
 Można modyfikować asocjacyjnej kolekcji. Pary klucz wartość są elementy mapy. Wyszukiwanie klucza można pobrać jej wartość skojarzoną i przechodzenie przez wszystkie pary klucz wartość, są obsługiwane.  
  
 `Map`i `MapView` są opartą na `<K, V, C = std::less<K>>`; w związku z tym komparatora można dostosować.  Ponadto `Vector` i `VectorView` są opartą na `<T, E = std::equal_to<T>>` tak, aby dostosować zachowanie `IndexOf()`. Jest to ważne głównie dla `Vector` i `VectorView` struktur wartość. Na przykład, aby utworzyć\<Windows::Foundation::DateTime >, należy podać niestandardowy komparatora ponieważ daty i godziny nie przeciążać == — operator.  
  
 [Platform::Collections::MapView, klasa](../cppcx/platform-collections-mapview-class.md)  
 Wersja tylko do odczytu do `Map`.  
  
 [Platform::Collections::Vector, klasa](../cppcx/platform-collections-vector-class.md)  
 Kolekcja sekwencji można modyfikować. `Vector<T>`obsługuje dostęp losowy czas stała i amortyzowanego stała time [Append](../cppcx/platform-collections-vector-class.md#append) operacji...  
  
 [Platform::Collections::VectorView, klasa](../cppcx/platform-collections-vectorview-class.md)  
 Wersja tylko do odczytu do `Vector`.  
  
 [Platform::Collections::InputIterator, klasa](../cppcx/platform-collections-inputiterator-class.md)  
 Iterator STL spełniająca wymagania STL iteratora wejściowego.  
  
 [Platform::Collections::VectorIterator, klasa](../cppcx/platform-collections-vectoriterator-class.md)  
 Iterator STL spełniająca wymagania STL modyfikowalną dostępie swobodnym iteratora.  
  
 [Platform::Collections::VectorViewIterator, klasa](../cppcx/platform-collections-vectorviewiterator-class.md)  
 Iterator STL, który spełnia wymagania STL `const` dostępie swobodnym iteratora.  
  
### <a name="begin-and-end-functions"></a>Funkcje BEGIN() i end()  
 Uproszczenie stosowania STL przetwarzania `Vector`, `VectorView`, `Map`, `MapView`i dowolnego `Windows::Foundation::Collections` obiektów C + +/ CX obsługuje przeciążeń [rozpocząć funkcja](../cppcx/begin-function.md) i [zakończenia Funkcja](../cppcx/end-function.md) funkcje niebędący elementem członkowskim.  
  
 W poniższej tabeli wymieniono dostępne Iteratory i funkcje.  
  
|Iteratory|Funkcje|  
|---------------|---------------|  
|[Platform::Collections::VectorIterator\<T >](../cppcx/platform-collections-vectoriterator-class.md)<br /><br /> (Wewnętrznie przechowuje [Windows::Foundation::Collections:: IVector\<T >](http://msdn.microsoft.com/library/windows/apps/br206631.aspx) i wewnętrznej)|[Rozpocznij](../cppcx/begin-function.md)/ [zakończenia](../cppcx/end-function.md)([Windows::Foundation::Collections:: IVector\<T >](http://msdn.microsoft.com/library/windows/apps/br206631.aspx))|  
|[Platform::Collections::VectorViewIterator\<T >](../cppcx/platform-collections-vectorviewiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IVectorView\<T >](http://msdn.microsoft.com/library/windows/apps/br226058.aspx)^ i wewnętrznej)|[Rozpocznij](../cppcx/begin-function.md)/ [zakończenia](../cppcx/end-function.md) ([IVectorView\<T >](http://msdn.microsoft.com/library/windows/apps/br226058.aspx)^)|  
|[Platform::Collections::InputIterator\<T >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IIterator\<T >](http://msdn.microsoft.com/library/windows/apps/br226026.aspx)^ i T.)|[Rozpocznij](../cppcx/begin-function.md)/ [zakończenia](../cppcx/end-function.md) ([IIterable\<T >](http://msdn.microsoft.com/library/windows/apps/br226024.aspx))|  
|[Platform::Collections::InputIterator < IKeyValuePair\<K, V > ^ >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IIterator\<T >](http://msdn.microsoft.com/library/windows/apps/br226026.aspx)^ i T.)|[Rozpocznij](../cppcx/begin-function.md)/ [zakończenia](../cppcx/end-function.md) ([IMap\<K, V >](http://msdn.microsoft.com/library/windows/apps/br226042.aspx).|  
|[Platform::Collections::InputIterator < IKeyValuePair\<K, V > ^ >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Wewnętrznie przechowuje [IIterator\<T >](http://msdn.microsoft.com/library/windows/apps/br226026.aspx)^ i T.)|[Rozpocznij](../cppcx/begin-function.md)/ [zakończenia](../cppcx/end-function.md) ([Windows::Foundation::Collections::IMapView](http://msdn.microsoft.com/library/windows/apps/br226037.aspx))|  
  
### <a name="collection-change-events"></a>Zdarzenia zmiany kolekcji  
 `Vector`i `Map` obsługuje wiązania danych w kolekcjach XAML zaimplementowanie zdarzeń występujących podczas zmiany obiektu kolekcji lub resetowania lub po wstawieniu dowolny element w kolekcji, usunięte lub zmodyfikowane. Napisania własnych typów tego wiązania z danymi pomocy technicznej, mimo że nie może dziedziczyć z `Map` lub `Vector` ponieważ te typy są zapieczętowane.  
  
 [Windows::Foundation::Collections::VectorChangedEventHandler](http://msdn.microsoft.com/library/windows/apps/br206656.aspx) i [Windows::Foundation::Collections::MapChangedEventHandler](http://msdn.microsoft.com/library/windows/apps/br206644.aspx) delegatów Określ podpisów dla obsługi zdarzeń zdarzenia zmiany kolekcji. [Windows::Foundation::Collections::CollectionChange](http://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx) klasy publicznym typie wyliczeniowym i `Platform::Collection::Details::MapChangedEventArgs` i `Platform::Collections::Details::VectorChangedEventArgs` klasy ref przechowywania argumenty zdarzeń, aby ustalić przyczynę zdarzenia. *`EventArgs` Typy są definiowane w `Details` przestrzeni nazw, ponieważ nie masz do utworzenia lub używać ich jawnie, gdy używasz `Map` lub `Vector`.  
  
## <a name="see-also"></a>Zobacz też  
 [System typów](../cppcx/type-system-c-cx.md)   
 [Typy wbudowane](http://msdn.microsoft.com/en-us/acc196fd-09da-4882-b554-6c94685ec75f)   
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)