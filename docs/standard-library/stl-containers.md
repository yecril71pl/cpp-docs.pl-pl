---
title: Kontenery biblioteki standardowej języka C++
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Standard Library, class template containers
- containers, C++ Standard Library
ms.assetid: 8e915ca1-19ba-4f0d-93c8-e2c3bfd638eb
ms.openlocfilehash: 01be754dd7b418f64cf495d7563f65b323265df8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376702"
---
# <a name="c-standard-library-containers"></a>Kontenery biblioteki standardowej języka C++

Biblioteka standardowa udostępnia różne kontenery typu bezpieczne do przechowywania kolekcji powiązanych obiektów. Kontenery są szablonami klas. Podczas deklarowania zmiennej kontenera, należy określić typ elementów, które kontener będzie przechowywać. Kontenery mogą być konstruowane z list inicjatora. Mają one funkcje członkowskie do dodawania i usuwania elementów i wykonywania innych operacji.

Można iterować nad elementami w kontenerze i uzyskać dostęp do poszczególnych elementów za pomocą [iteratorów](../standard-library/iterators.md). Iteratorów można używać jawnie przy użyciu ich funkcji członkowskich i operatorów i funkcji globalnych. Można również użyć ich niejawnie, na przykład za pomocą pętli zakres dla. Iteratory dla wszystkich kontenerów biblioteki standardowej języka C++ mają wspólny interfejs, ale każdy kontener definiuje własne wyspecjalizowane iteratory.

Kontenery można podzielić na trzy kategorie: kontenery sekwencji, kontenery zespolone i adaptery kontenerów.

## <a name="sequence-containers"></a><a name="sequence_containers"></a>Kontenery sekwencji

Kontenery sekwencji zachowują kolejność wstawianych elementów, które określisz.

`vector` Kontener zachowuje się jak tablica, ale może automatycznie rosnąć zgodnie z wymaganiami. Jest to dostęp losowy i stale przechowywane, a długość jest bardzo elastyczna. Z tych powodów `vector` i więcej, jest preferowanym kontenerem sekwencji dla większości aplikacji. W razie wątpliwości co do tego, jakiego rodzaju kontener sekwencji użyć, zacznij od użycia wektora! Aby uzyskać więcej informacji, zobacz [Klasa wektorowa](../standard-library/vector-class.md).

Pojemnik `array` ma niektóre z mocnych `vector`stron , ale długość nie jest tak elastyczna. Aby uzyskać więcej informacji, zobacz [klasa tablicy](../standard-library/array-class-stl.md).

Kontener `deque` (kolejki dwustronnej) umożliwia szybkie wstawianie i usuwanie na początku i na końcu kontenera. Dzieli się z możliwościami losowego dostępu `vector`i elastycznej długości , ale nie jest ciągły. Aby uzyskać więcej informacji, zobacz [deque Class](../standard-library/deque-class.md).

`list` Kontener jest podwójnie połączone listy, która umożliwia dwukierunkowy dostęp, szybkie wstawienia i szybkie usunięcia w dowolnym miejscu w kontenerze, ale nie można losowo uzyskać dostęp do elementu w kontenerze. Aby uzyskać więcej informacji, zobacz [listę Klasy](../standard-library/list-class.md).

`forward_list` Kontener jest pojedynczo połączona lista — wersja `list`dostępu do przodu . Aby uzyskać więcej informacji, zobacz [forward_list Klasa](../standard-library/forward-list-class.md).

## <a name="associative-containers"></a>Kontenery zespolające

W kontenerach zespolonych elementy są wstawiane w wstępnie zdefiniowanej kolejności — na przykład jako posortowane rosnąco. Dostępne są również nieuiarszone kontenery zespolone. Kontenery zespolone można podzielić na dwa podzbiory: mapy i zestawy.

A `map`, czasami określane jako słownik, składa się z pary klucz/wartość. Klucz jest używany do kolejności sekwencji, a wartość jest skojarzona z tym kluczem. Na przykład `map` może zawierać klucze, które reprezentują każde unikatowe słowo w tekście i odpowiadające im wartości, które reprezentują liczbę razy, że każdy wyraz pojawia się w tekście. Nieuiszczona wersja `map` `unordered_map`jest . Aby uzyskać więcej informacji, zobacz [mapę Klasa](../standard-library/map-class.md) i [unordered_map Klasa](../standard-library/unordered-map-class.md).

A `set` jest tylko rosnącym kontenerem unikatowych elementów — wartość jest również kluczem. Nieuiszczona wersja `set` `unordered_set`jest . Aby uzyskać więcej informacji, zobacz [ustawianie klasy](../standard-library/set-class.md) i [unordered_set klasy](../standard-library/unordered-set-class.md).

Oba `map` `set` i zezwalaj tylko na wstawianie do kontenera tylko jednego wystąpienia klucza lub elementu. Jeśli wymagane jest wiele wystąpień `multimap` elementów, należy użyć lub `multiset`. Wersje nieurządzone `unordered_multimap` są `unordered_multiset`i . Aby uzyskać więcej informacji, zobacz [klasa multimap](../standard-library/multimap-class.md), [unordered_multimap klasa,](../standard-library/unordered-multimap-class.md) [klasa multiset](../standard-library/multiset-class.md)i [klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Uporządkowane mapy i zestawy obsługują dwukierunkowe iteratory, a ich nieurządzone odpowiedniki obsługują iteratory do przodu. Aby uzyskać więcej informacji, zobacz [Iteratory](../standard-library/iterators.md).

### <a name="heterogeneous-lookup-in-associative-containers-c14"></a>Heterogeniczne wyszukiwanie w kontenerach zespolonych (C++14)

Uporządkowane kontenery zespolone (mapa, multimapa, zestaw i zestaw wielozespoły) obsługują teraz heterogeniczne wyszukiwanie, co oznacza, że nie trzeba `find()` `lower_bound()`już przechodzić dokładnie tego samego typu obiektu co klucz lub element w funkcjach członkowskich, takich jak i . Zamiast tego można przekazać dowolny typ, dla `operator<` którego jest zdefiniowany przeciążony, który umożliwia porównanie do typu klucza.

Heterogeniczne wyszukiwanie jest włączone na zasadzie opt-in `std::less<>` po `std::greater<>` określeniu komparatora lub "diamond functor" podczas deklarowania zmiennej kontenera, jak pokazano poniżej:

```cpp
std::set<BigObject, std::less<>> myNewSet;
```

Jeśli używasz domyślnego komparatora, kontener zachowuje się dokładnie tak, jak w języku C++ 11 i wcześniejszych.

W poniższym przykładzie `operator<` pokazano, jak `std::set` przeciążenie, aby umożliwić użytkownikom wyszukiwania do po prostu przekazując `BigObject::id` w małym ciągu, który można porównać do każdego elementu członkowskiego obiektu.

```cpp
#include <set>
#include <string>
#include <iostream>
#include <functional>

using namespace std;

class BigObject
{
public:
    string id;
    explicit BigObject(const string& s) : id(s) {}
    bool operator< (const BigObject& other) const
    {
        return this->id < other.id;
    }

    // Other members....
};

inline bool operator<(const string& otherId, const BigObject& obj)
{
    return otherId < obj.id;
}

inline bool operator<(const BigObject& obj, const string& otherId)
{
    return obj.id < otherId;
}

int main()
{
    // Use C++14 brace-init syntax to invoke BigObject(string).
    // The s suffix invokes string ctor. It is a C++14 user-defined
    // literal defined in <string>
    BigObject b1{ "42F"s };
    BigObject b2{ "52F"s };
    BigObject b3{ "62F"s };
    set<BigObject, less<>> myNewSet; // C++14
    myNewSet.insert(b1);
    myNewSet.insert(b2);
    myNewSet.insert(b3);
    auto it = myNewSet.find(string("62F"));
    if (it != myNewSet.end())
        cout << "myNewSet element = " << it->id << endl;
    else
        cout << "element not found " << endl;

    // Keep console open in debug mode:
    cout << endl << "Press Enter to exit.";
    string s;
    getline(cin, s);
    return 0;
}

//Output: myNewSet element = 62F
```

Następujące funkcje członkowskie na mapie, multimapie, zestawie i zestawie wielokrotnym zostały przeciążone w celu obsługi heterogenicznych odnośeń:

1. find

1. count

1. lower_bound

1. upper_bound

1. equal_range

## <a name="container-adapters"></a>Adaptery kontenerów

Karta kontenera jest odmianą sekwencji lub kontenera zespolonego, który ogranicza interfejs dla prostoty i przejrzystości. Karty kontenerów nie obsługują iteratorów.

Kontener `queue` następuje FIFO (pierwszy w, pierwszy na zewnątrz) semantyka. Pierwszy *wypchnięty*element — czyli wstawiony do kolejki — jest pierwszym, który zostanie *wysunięty*— czyli usunięty z kolejki. Aby uzyskać więcej informacji, zobacz [kolejka klasa](../standard-library/queue-class.md).

`priority_queue` Kontener jest zorganizowany w taki sposób, że element, który ma najwyższą wartość jest zawsze pierwszy w kolejce. Aby uzyskać więcej informacji, zobacz [priority_queue Class](../standard-library/priority-queue-class.md).

Kontener `stack` następuje LIFO (last in, first out) semantyka. Ostatni element wypchnięty na stosie jest pierwszym elementem. Aby uzyskać więcej informacji, zobacz [stack Class](../standard-library/stack-class.md).

Ponieważ karty kontenerów nie obsługują iteratorów, nie można ich używać z algorytmami biblioteki standardowej języka C++. Aby uzyskać więcej informacji, zobacz [Algorytmy](../standard-library/algorithms.md).

## <a name="requirements-for-container-elements"></a>Wymagania dotyczące elementów kontenera

Ogólnie rzecz biorąc elementy wstawione do kontenera biblioteki standardowej języka C++ może mieć prawie dowolny typ obiektu, jeśli można je kopiować. Elementy tylko do ruchomych — na `vector<unique_ptr<T>>` przykład takie, `unique_ptr<>` które są tworzone przy użyciu, będą działać tak długo, jak długo nie będziesz wywoływać funkcji członkowskich, które próbują je skopiować.

Destruktor nie może zgłaszać wyjątek.

Uporządkowane kontenery zespolone — opisane wcześniej w tym artykule — muszą mieć zdefiniowany operator porównania publicznego. (Domyślnie operator jest `operator<`, ale nawet typy, `operator<` które nie działają z są obsługiwane.

Niektóre operacje na kontenerach może również wymagać konstruktora domyślnego publicznego i operatora równoważności publicznej. Na przykład nieuiszczone kontenery zespolone wymagają obsługi równości i mieszania.

## <a name="accessing-container-elements"></a>Uzyskiwanie dostępu do elementów kontenera

Elementy kontenerów są dostępne za pomocą iteratorów. Aby uzyskać więcej informacji, zobacz [Iteratory](../standard-library/iterators.md).

> [!NOTE]
> Można również użyć [oparte na zakresie dla pętli](../cpp/range-based-for-statement-cpp.md) do iteracji za pomocą kolekcji biblioteki standardowej języka C++.

## <a name="comparing-containers"></a>Porównywanie kontenerów

Wszystkie kontenery przeciążają operator== do porównywania dwóch kontenerów tego samego typu, które mają ten sam typ elementu. Za pomocą _= można porównać\<ciąg wektorowy> z\<inną ciągiem wektorowym>, ale nie można\<jej użyć do porównania\<ciągu wektorowego> z\<> ciągu listy lub ciągu\<wektorowego> do znaku wektorowego*>.  W języku C++98/03 można użyć [std::equal](algorithm-functions.md#equal) lub [std::mismatch](algorithm-functions.md#mismatch) do porównania różnych typów kontenerów i/lub typów elementów. W języku C++11 można również użyć [std::is_permutation](algorithm-functions.md#is_permutation). Ale we wszystkich tych przypadkach funkcje zakładają, że kontenery mają taką samą długość. Jeśli drugi zakres jest krótszy niż pierwszy, następnie wyniki niezdefiniowanego zachowania. Jeśli drugi zakres jest dłuższy, wyniki mogą być nadal niepoprawne, ponieważ porównanie nigdy nie jest kontynuowane po zakończeniu pierwszego zakresu.

### <a name="comparing-dissimilar-containers-c14"></a>Porównanie różnych pojemników (C++14)

W języku C++14 i nowszych można porównać różne kontenery i/lub różne typy elementów przy użyciu jednego z przeciążeń funkcji `std::equal`, `std::mismatch`lub `std::is_permutation` funkcji, które zajmują dwa pełne zakresy. Te przeciążenia umożliwiają porównywanie kontenerów o różnych długościach. Te przeciążenia są znacznie mniej podatne na błędy użytkownika i są zoptymalizowane do zwracania false w stałym czasie, gdy kontenery o różnych długościach są porównywane. W związku z tym zaleca się używać tych przeciążeń, chyba że masz wyraźny powód, aby nie lub używasz [kontenera std::list,](../standard-library/list-class.md) który nie korzysta z optymalizacji podwójnego zakresu.

## <a name="see-also"></a>Zobacz też

[Kontenery równoległe](../parallel/concrt/parallel-containers-and-objects.md)\
[\<>pojemnika próbki](../standard-library/sample-container.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
