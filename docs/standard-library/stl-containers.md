---
title: Kontenery biblioteki C++ Standard | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: fd851ae3cf47ca260b1923d969123b21293d8623
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862432"
---
# <a name="c-standard-library-containers"></a>Kontenery biblioteki C++ Standard

Standardowa biblioteka zawiera różne kontenery bezpieczny do przechowywania kolekcji powiązanych obiektów. Kontenery są szablony klas; Deklaracja zmiennej kontenera, musisz wybrać typ elementów, które będą przechowywane w kontenerze. Kontenery może być skonstruowany z listy inicjatorów. Mają one funkcje Członkowskie Dodawanie i usuwanie elementów oraz wykonywania innych operacji.

Iteracja elementów w kontenerze, a dostęp do poszczególnych elementów za pomocą [Iteratory](../standard-library/iterators.md). Iteratory można użyć jawnie, przy użyciu ich funkcji Członkowskich i operatory także funkcje globalne. Można również używać ich niejawnie, na przykład przy użyciu zakresu-pętli for. Iteratory dla wszystkich kontenerów standardowa biblioteka C++ mają wspólny interfejs, ale własne specjalistyczne Iteratory definiuje każdego kontenera.

Kontenery mogą być podzielone na trzy kategorie: sekwencji kontenerów, asocjacyjnej kontenery i kart kontenera.

## <a name="sequence_containers"></a> Kontenery sekwencji

Kontenery sekwencji Obsługa kolejności wstawionych elementów należy określić.

A `vector` kontenera zachowuje się jak tablicy, ale może zwiększyć się automatycznie zgodnie z wymaganiami. Jest dostęp losowy i przechowywane ciągłym, a długość jest bardzo elastyczny. Z tego względu i więcej `vector` kontener preferowaną kolejność dla większości aplikacji. W przypadku wątpliwości jakiego rodzaju sekwencji kontener do użycia, uruchomić za pomocą wektora! Aby uzyskać więcej informacji, zobacz [vector — klasa](../standard-library/vector-class.md).

`array` Kontener ma niektóre silnych `vector`, ale nie jako elastyczne długość. Aby uzyskać więcej informacji, zobacz [array — klasa](../standard-library/array-class-stl.md).

A `deque` kontenera (kolejka została zakończona podwójnego) pozwala na szybkie wstawienia i usunięcia na początku i na końcu kontenera. Współużytkuje zalety dostęp losowy i elastycznej długości `vector`, ale nie jest ciągły. Aby uzyskać więcej informacji, zobacz [deque — klasa](../standard-library/deque-class.md).

A `list` kontenera jest podwójnie połączonej listy umożliwiającą dostęp dwukierunkowego, szybkie wstawienia i szybkiego usunięcia dowolne miejsce w kontenerze, ale losowo nie masz dostępu do elementu w kontenerze. Aby uzyskać więcej informacji, zobacz [list — klasa](../standard-library/list-class.md).

A `forward_list` kontenera jest pojedynczo połączonej listy — wersja dostępu do przodu `list`. Aby uzyskać więcej informacji, zobacz [forward_list — klasa](../standard-library/forward-list-class.md).

## <a name="associative-containers"></a>Kontenery asocjacyjnej

W kontenerach asocjacyjnej elementy są wstawiane do wstępnie zdefiniowanej kolejności — na przykład jako rosnącej posortowane. Dostępne są również nieuporządkowaną asocjacyjnej kontenerów. Asocjacyjnej kontenery, można podzielić na dwa podzestawy: mapuje i ustawia.

A `map`, czasami określane jako słownik, składa się z pary klucz wartość. Ten klucz jest używany w celu ustalenia sekwencji, a wartość jest skojarzony z tym kluczem. Na przykład `map` może zawierać kluczy, które reprezentują unikatowy wyrazów tekst i odpowiadające im wartości reprezentujących liczbę każdego wyrazu pojawia się w tekście. Wersja nieuporządkowaną `map` jest `unordered_map`. Aby uzyskać więcej informacji, zobacz [map — klasa](../standard-library/map-class.md) i [unordered_map — klasa](../standard-library/unordered-map-class.md).

A `set` jest po prostu rosnącej kontenera elementy unikatowe — wartość jest także klucz. Wersja nieuporządkowaną `set` jest `unordered_set`. Aby uzyskać więcej informacji, zobacz [Ustaw klasy](../standard-library/set-class.md) i [unordered_set — klasa](../standard-library/unordered-set-class.md).

Zarówno `map` i `set` Zezwalaj tylko jedno wystąpienie klucza lub element ma zostać wstawiony do kontenera. Jeśli wymaganych jest wiele wystąpień elementów, użyj `multimap` lub `multiset`. Wersje nieuporządkowaną `unordered_multimap` i `unordered_multiset`. Aby uzyskać więcej informacji, zobacz [multimap — klasa](../standard-library/multimap-class.md), [unordered_multimap — klasa](../standard-library/unordered-multimap-class.md), [multiset — klasa](../standard-library/multiset-class.md), i [unordered_multiset — klasa](../standard-library/unordered-multiset-class.md).

Mapy uporządkowane i ustawia obsługuje Iteratory dwukierunkowe, a ich odpowiedniki nieuporządkowaną obsługuje Iteratory do przodu. Aby uzyskać więcej informacji, zobacz [Iteratory](../standard-library/iterators.md).

### <a name="heterogeneous-lookup-in-associative-containers-c14"></a>Heterogenicznych wyszukiwanie w kontenerach asocjacyjnej (C ++ 14)

Uporządkowane asocjacyjnej kontenery (mapy, multimap i zestaw wielokrotny) teraz heterogenicznych Wyszukiwanie pomocy technicznej, co oznacza, że nie jesteś już wymagane do przekazania dokładnie jeden typ obiektów jako klucz lub element w funkcji elementów członkowskich, takich jak `find()` i `lower_bound()` . Zamiast tego można przekazać dowolnego typu, dla którego przeciążone `operator<` jest zdefiniowany, który umożliwia porównanie z typem klucza.

Włączono heterogenicznych wyszukiwanie na podstawie opt po określeniu `std::less<>` lub `std::greater<>` "romboidalny obiekt" komparatora przy deklarowaniu zmiennej kontenera, jak pokazano poniżej:

```cpp
std::set<BigObject, std::less<>> myNewSet;
```

Jeśli używasz komparatora domyślnego kontenera zachowuje się dokładnie tak jak w języku C ++ 11 i starszych wersji.

Poniższy przykład przedstawia sposób przeciążenia `operator<` w celu umożliwienia użytkownikom `std::set` przeprowadzenie wyszukiwania po prostu przekazując w małych ciąg, który można porównać do każdego obiektu `BigObject::id` elementu członkowskiego.

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

Następujący element członkowski funkcje w mapie multimap —, zestaw i multiset zostały przeciążone w celu obsługi heterogenicznych wyszukiwania:

1. find

1. count

1. lower_bound

1. upper_bound

1. equal_range

## <a name="container-adapters"></a>Kontener kart

Karta kontenera jest odmianą sekwencji lub asocjacyjnej kontener, który ogranicza interfejs dla uproszczenia i przejrzystości. Kontener karty nie obsługują Iteratory.

A `queue` kontenera następuje semantyki FIFO (pierwszy na, pierwszy na wyjściu). Pierwszy element *wypchniętych*— to znaczy wstawionych do kolejki — jest pierwszą osobą, która jest *zdjęte ze stosu*— to znaczy usuniętych z kolejki. Aby uzyskać więcej informacji, zobacz [kolejka klasy](../standard-library/queue-class.md).

A `priority_queue` kontenera jest zorganizowana w taki sposób, że element, który ma najwyższą wartość jest zawsze pierwszy w kolejce. Aby uzyskać więcej informacji, zobacz [priority_queue — klasa](../standard-library/priority-queue-class.md).

A `stack` kontenera następuje semantyki LIFO (ostatnie w pierwszej kolejności). Ostatni element wypychana na stosie jest pierwszym elementem zdjęte ze stosu. Aby uzyskać więcej informacji, zobacz [stack — klasa](../standard-library/stack-class.md).

Ponieważ karty kontenera nie obsługują Iteratory, nie można używać z algorytmów standardowa biblioteka C++. Aby uzyskać więcej informacji, zobacz [algorytmy](../standard-library/algorithms.md).

## <a name="requirements-for-container-elements"></a>Wymagania dotyczące elementów kontenera

Ogólnie rzecz biorąc elementy do kontenera standardowa biblioteka C++ może być dowolnego typu obiektu, jeśli są one copyable. Tylko do ruchome elementów — na przykład tych, takich jak `vector<unique_ptr<T>>` które są tworzone przy użyciu `unique_ptr<>` będzie działać, dopóki nie wywołać elementu członkowskiego funkcje, które próbują skopiuj je.

Destruktor nie można zgłosić wyjątek.

Uporządkowane asocjacyjnej kontenery — opisane w tym artykule — musi mieć zdefiniowany operator porównania publicznego. (Domyślnie jest operator `operator<`, ale nawet typy, które nie działają z `operator<` są obsługiwane.

Niektóre operacje kontenerów może wymagać publicznego konstruktora domyślnego i operatora równoważność publicznego. Na przykład nieuporządkowaną kontenery asocjacyjnej wymaga obsługi równości i tworzenia skrótów.

## <a name="accessing-container-elements"></a>Uzyskiwanie dostępu do kontenera elementów

Elementy kontenery są dostępne za pomocą Iteratory. Aby uzyskać więcej informacji, zobacz [Iteratory](../standard-library/iterators.md).

> [!NOTE]
> Można również użyć [na podstawie zakresu dla pętli](../cpp/range-based-for-statement-cpp.md) do wykonywania iteracji kolekcji standardowa biblioteka C++.

## <a name="comparing-containers"></a>Porównywanie kontenerów

Wszystkie kontenery przeciążyć operator == do porównywania dwóch kontenerów tego samego typu, które mają ten sam typ elementu. Można użyć == do porównania wektora\<ciąg > do innego wektor\<ciąg >, ale nie można go użyć do porównania wektora\<ciąg > do listy\<ciąg > lub wektora\<ciągu > do wektora \<char * >.  W języku C ++ 98/03 służy [std::equal](algorithm-functions.md#equal) lub [std::mismatch](algorithm-functions.md#mismatch) do porównania kontenera różnych typów i/lub typów elementów. W języku C ++ 11 umożliwia także [std::is_permutation](algorithm-functions.md#is_permutation). Jednak w tych przypadkach funkcje założono, że kontenery mają tę samą długość. Jeśli drugi zakres jest krótszy niż pierwszy, a następnie niezdefiniowane zachowanie wyników. Jeśli drugi zakres jest dłuższy, wyniki mogą nadal być nieprawidłowy, ponieważ porównanie nigdy nie będzie kontynuowane poza końcem pierwszego zakresu.

### <a name="comparing-dissimilar-containers-c14"></a>Porównanie różnych kontenerów (C ++ 14)

W języku C ++ 14 i nowszych możesz porównać różnych kontenerów i/lub elementy różnych typów przy użyciu jednej z **std::equal**, **std::mismatch**, lub **std::is_permutation**funkcji przeciążeń, które przyjmują dwa zakresy ukończone. Te przeciążenia umożliwiają porównanie kontenerów różne długości. Te przeciążenia są znacznie mniej podatny na błędy użytkowników i są optymalizowane w celu zwróci wartość false w czasie stałej, gdy są porównywane kontenery niepodobnych długości. Dlatego zaleca się użyć tych przeciążenia, chyba że (1) masz oczywiste Przyczyna nie lub (2) w przypadku korzystania [kontener std::list](../standard-library/list-class.md) kontenera, który nie korzysta z dwóch zakres optymalizacji.

## <a name="see-also"></a>Zobacz także

[Kontenery](../cpp/containers-modern-cpp.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
[\<Przykładowy kontener >](../standard-library/sample-container.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
