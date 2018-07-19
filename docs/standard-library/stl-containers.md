---
title: Kontenery standardowej biblioteki C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- C++ Standard Library, template class containers
- containers, C++ Standard Library
ms.assetid: 8e915ca1-19ba-4f0d-93c8-e2c3bfd638eb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3b758c5db483f74ddb43031ab41f2d2b46514e4
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965245"
---
# <a name="c-standard-library-containers"></a>Kontenery standardowej biblioteki C++

Standardowa biblioteka zapewnia różne kontenery bezpieczny do przechowywania kolekcji powiązanych obiektów. Pojemniki to klasy szablonów; Kiedy Deklarujesz zmienną kontenera, określasz typ elementów, które będą przechowywane w kontenerze. Kontenery można skonstruować z listami inicjatorów. Mają one funkcji elementów członkowskich do dodawania i usuwania elementów i wykonywania innych operacji.

Iteracja elementów w kontenerze, a dostęp do poszczególnych elementów za pomocą [Iteratory](../standard-library/iterators.md). Używania iteratorów jawnie za pomocą swoich elementów członkowskich i operatorów także funkcje globalne. Możesz ich użyć także niejawnie, na przykład za pomocą zakresu-pętli for. Iteratory na wszystkie kontenery standardowej biblioteki języka C++ mają wspólny interfejs, ale każdy kontener definiuje swój własny wyspecjalizowane Iteratory.

Kontenery można podzielić na trzy kategorie: sekwencji, kontenerów, kontenerów asocjacyjnych i kart kontenera.

## <a name="sequence_containers"></a> Kontenery sekwencji

Kontenery sekwencji zachowują określoną kolejność wstawionych elementów należy określić.

A `vector` kontenera, który zachowuje się jak tablica, ale może się automatycznie powiększać stosownie do potrzeb. Jest swobodnego dostępu i przechowywane w sposób ciągły, a długość jest bardzo elastyczna. Dla tych i innych, powodów `vector` jest preferowanym kontenerem sekwencyjnym dla większości aplikacji. W razie wątpliwości dotyczące rodzaju kontenerem sekwencyjnym do użycia, należy uruchomić za pomocą wektora! Aby uzyskać więcej informacji, zobacz [vector, klasa](../standard-library/vector-class.md).

`array` Kontener ma niektóre zalety `vector`, ale długość nie jest tak elastyczna. Aby uzyskać więcej informacji, zobacz [array, klasa](../standard-library/array-class-stl.md).

A `deque` kontenera (kolejki dwustronnej) pozwala na szybkie wstawienia i usunięcia na początku i na końcu kontenera. Współdzieli dostępu swobodnego i elastycznej długości zalety `vector`, ale nie jest ciągły. Aby uzyskać więcej informacji, zobacz [klasę deque](../standard-library/deque-class.md).

A `list` kontenera jest podwójnie połączoną listą umożliwiającą dostęp dwukierunkowy, szybkie wstawienia i szybkie usunięcia gdziekolwiek w kontenerze, ale losowego nie masz dostępu do elementu w kontenerze. Aby uzyskać więcej informacji, zobacz [list, klasa](../standard-library/list-class.md).

A `forward_list` kontener jest pojedynczo połączoną listą — dostępu do przodu wersję `list`. Aby uzyskać więcej informacji, zobacz [forward_list — klasa](../standard-library/forward-list-class.md).

## <a name="associative-containers"></a>Kontenery asocjacyjne

W kontenerach asocjacyjnych elementy są wstawiane w kolejności wstępnie zdefiniowanej — na przykład, jako posortowanej rosnąco. Dostępne są także nieuporządkowane kontenery asocjacyjne. Kontenery asocjacyjne można podzielić na dwa podzbiory: mapy i zestawy.

A `map`, czasami określany jako słownik, składa się z pary klucz/wartość. Klucz jest używany w celu ustalenia sekwencji, a wartość jest skojarzona z tym kluczem. Na przykład `map` może zawierać klucze, które reprezentują każde unikatowe słowo w tekście i odpowiadające im wartości, które reprezentują liczbę wystąpień każdego wyrazu w tekście. Nieuporządkowana wersja `map` jest `unordered_map`. Aby uzyskać więcej informacji, zobacz [map — klasa](../standard-library/map-class.md) i [unordered_map, klasa](../standard-library/unordered-map-class.md).

Element `set` jest tylko uporządkowany rosnąco kontenerem unikatowych elementów — wartość jest także kluczem. Nieuporządkowana wersja `set` jest `unordered_set`. Aby uzyskać więcej informacji, zobacz [set — klasa](../standard-library/set-class.md) i [unordered_set, klasa](../standard-library/unordered-set-class.md).

Zarówno `map` i `set` Zezwalaj tylko jednego wystąpienia klucza lub element ma zostać wstawiony do kontenera. Jeśli wymaganych jest wiele instancji elementów, użyj `multimap` lub `multiset`. Nieuporządkowane wersje to `unordered_multimap` i `unordered_multiset`. Aby uzyskać więcej informacji, zobacz [multimap — klasa](../standard-library/multimap-class.md), [unordered_multimap, klasa](../standard-library/unordered-multimap-class.md), [multiset — klasa](../standard-library/multiset-class.md), i [unordered_multiset, klasa](../standard-library/unordered-multiset-class.md).

Uporządkowane mapy i zestawy obsługują Iteratory dwukierunkowe, a ich nieuporządkowane odpowiedniki obsługują Iteratory postępujące. Aby uzyskać więcej informacji, zobacz [Iteratory](../standard-library/iterators.md).

### <a name="heterogeneous-lookup-in-associative-containers-c14"></a>Heterogeniczne wyszukiwanie w kontenerach asocjacyjnych (C ++ 14)

Uporządkowane kontenery asocjacyjne (mapa, mapa wielokrotna, zestaw i multiset) teraz heterogeniczne Wyszukiwanie pomocy technicznej, co oznacza, że nie jesteś już konieczne zakończenie ich powodzeniem dokładnie ten sam typ obiektu jako klucza lub elementu w funkcji elementów członkowskich, takich jak `find()` i `lower_bound()` . Zamiast tego można przekazać dowolny typ, dla którego przeciążony `operator<` jest zdefiniowany, który umożliwia porównanie z typem klucza.

Włączono heterogenicznych wyszukiwanie na podstawie zgłoszenie zgody na uczestnictwo, po określeniu `std::less<>` lub `std::greater<>` "romboidalna funktor" komparator podczas deklarowania zmiennej kontenera, jak pokazano poniżej:

```cpp
std::set<BigObject, std::less<>> myNewSet;
```

Jeśli używasz komparator domyślne, kontener zachowuje się dokładnie tak jak w języku C ++ 11 i jego starszych wersji.

Poniższy przykład pokazuje, jak przeciążenia `operator<` w celu umożliwienia użytkownikom `std::set` celu wyszukiwań po prostu, przekazując ciąg małych, który można porównać do każdego obiektu `BigObject::id` elementu członkowskiego.

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

Następujący element członkowski funkcji w mapie multimap, zestawu i multiset mają zostać przeciążone, aby obsługiwać heterogeniczne wyszukiwanie:

1. find

1. count

1. lower_bound

1. upper_bound

1. equal_range

## <a name="container-adapters"></a>Karty kontenera

Adapter kontenera jest odmianą sekwencji lub asocjacyjnego kontenera, który ogranicza interfejs dla prostoty i jasności. Karty kontenera nie obsługują iteratorów.

A `queue` kontenera używa semantyki FIFO (pierwszy na wejściu, pierwszy na wyjściu). Pierwszy element *wypchnięcie*— czyli wstawiony do kolejki — jest pierwszym, który zostanie *zdjęte ze stosu*— to znaczy usunięty z kolejki. Aby uzyskać więcej informacji, zobacz [kolejkowania klasy](../standard-library/queue-class.md).

A `priority_queue` kontenera jest zorganizowana w taki sposób, że element, który ma najwyższą wartość, zawsze jest pierwszy w kolejce. Aby uzyskać więcej informacji, zobacz [priority_queue — klasa](../standard-library/priority-queue-class.md).

A `stack` kontenera używa semantyki LIFO (ostatni na wejściu, pierwszy na wyjściu). Ostatni element wypchnięty na stos jest pierwszym elementem zdjętym. Aby uzyskać więcej informacji, zobacz [stack — klasa](../standard-library/stack-class.md).

Ponieważ adaptery kontenera nie obsługują iteratorów, nie można używać z algorytmami standardowej biblioteki języka C++. Aby uzyskać więcej informacji, zobacz [algorytmy](../standard-library/algorithms.md).

## <a name="requirements-for-container-elements"></a>Wymagania dotyczące elementów kontenera

Ogólnie rzecz biorąc elementy wstawione w pojemniku standardowej biblioteki języka C++ może być dowolnego typu obiektu, jeśli są one do kopiowania. Elementy wyłącznie ruchome — na przykład tych, takie jak `vector<unique_ptr<T>>` , są tworzone za pomocą `unique_ptr<>` będzie działać tak długo, jak element członkowski nie wywołanie funkcji, które spróbuje je skopiować.

Zgłoś wyjątek, destruktor nie jest dozwolone.

Uporządkowane kontenery asocjacyjne — opisane wcześniej w tym artykule — muszą mieć zdefiniowany publiczny operator porównania. (Domyślnie jest operator `operator<`, ale nawet typy, które nie działają z `operator<` są obsługiwane.

Niektóre operacje na kontenerach również mogą wymagać publicznego konstruktora domyślnego i publicznego operatora równoważności. Na przykład nieuporządkowane kontenery asocjacyjne wymagają obsługi równości i mieszania.

## <a name="accessing-container-elements"></a>Uzyskiwanie dostępu do elementów kontenera

Elementy kontenery są dostępne przy użyciu iteratorów. Aby uzyskać więcej informacji, zobacz [Iteratory](../standard-library/iterators.md).

> [!NOTE]
> Można również użyć [zakresu pętli for opierających](../cpp/range-based-for-statement-cpp.md) do wykonywania iteracji w kolekcji standardowej biblioteki języka C++.

## <a name="comparing-containers"></a>Porównywanie kontenerów

Wszystkie kontenery przeciążenia operatora == do porównywania dwóch kontenerów tego samego typu, które mają ten sam typ elementu. Można użyć == do porównania wektor\<ciągu > do innego wektora\<ciągu >, można użyć, aby porównać wektor\<ciągu > do listy\<ciągu > lub wektor\<ciągu > do wektora \<char * >.  W języku C ++ 98/03 można użyć [std::equal](algorithm-functions.md#equal) lub [std::mismatch](algorithm-functions.md#mismatch) do porównania kontenera różne typy i/lub typy elementów. W języku C ++ 11 można również użyć [std::is_permutation](algorithm-functions.md#is_permutation). Jednak w takich przypadkach funkcje przyjęto założenie, że kontenery mają taką samą długość. Jeśli drugi zakres jest krótszy niż wyniki pierwszego, a następnie niezdefiniowane zachowanie. W przypadku dłużej drugiego zakresu, wyniki nadal można niepoprawne, ponieważ porównania nigdy nie będzie się powtarzał poza końcem pierwszego zakresu.

### <a name="comparing-dissimilar-containers-c14"></a>Porównywanie różnych kontenerów (C ++ 14)

W języku C ++ 14 i nowszych możesz porównać różnych kontenerów i/lub typów danych elementów niepodobnych przy użyciu jednej z `std::equal`, `std::mismatch`, lub `std::is_permutation` funkcji przeciążeń, które przyjmują dwa zakresy ukończone. Te przeciążone funkcje umożliwiają porównanie kontenerów przy użyciu różnej długości. Te przeciążenia są znacznie mniej podatny na błędy użytkowników i są zoptymalizowane pod kątem zwróci wartość false w stałym czasie, gdy są porównywane kontenery różne długości. Dlatego zaleca się używać tych przeciążeń, chyba że (1) użytkownik nie ma oczywiste przyczyna lub (2) w przypadku korzystania [kontener std::list](../standard-library/list-class.md) kontenera, które nie korzystają z optymalizacji dwuzakresowymi.

## <a name="see-also"></a>Zobacz także

[Kontenery](../cpp/containers-modern-cpp.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
[\<Przykładowy kontener >](../standard-library/sample-container.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
