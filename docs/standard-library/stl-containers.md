---
title: C++Kontenery biblioteki standardowej
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Standard Library, template class containers
- containers, C++ Standard Library
ms.assetid: 8e915ca1-19ba-4f0d-93c8-e2c3bfd638eb
ms.openlocfilehash: 6077ff76e04e6f078946eed0856723e2a9998f58
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449595"
---
# <a name="c-standard-library-containers"></a>C++Kontenery biblioteki standardowej

Biblioteka standardowa zawiera różne bezpieczne dla typu kontenery umożliwiające przechowywanie kolekcji powiązanych obiektów. Kontenery są szablonami klas; podczas deklarowania zmiennej kontenera należy określić typ elementów, które będą przechowywane w kontenerze. Kontenery można utworzyć przy użyciu list inicjatorów. Mają one funkcje członkowskie do dodawania i usuwania elementów oraz wykonywania innych operacji.

Wykonujesz iterację elementów w kontenerze i uzyskuj dostęp do poszczególnych elementów za pomocą [iteratorów](../standard-library/iterators.md). Iteratorów można użyć jawnie przy użyciu ich funkcji składowych i operatorów oraz funkcji globalnych. Można ich również użyć niejawnie, na przykład za pomocą pętli Range for. Iteratory dla wszystkich C++ kontenerów biblioteki standardowej mają wspólny interfejs, ale każdy kontener definiuje własne Iteratory.

Kontenery można podzielić na trzy kategorie: Kontenery sekwencji, Kontenery asocjacyjne i karty kontenerów.

## <a name="sequence_containers"></a>Kontenery sekwencji

Kontenery sekwencji zachowują porządkowanie wstawionych elementów, które określisz.

`vector` Kontener zachowuje się jak tablica, ale może zostać automatycznie powiększony zgodnie z potrzebami. Jest to dostęp losowy i ciągły, a długość jest wysoce elastyczna. Z tego względu, `vector` jest preferowanym kontenerem sekwencji dla większości aplikacji. W razie wątpliwości co do jakiego rodzaju kontenera sekwencji należy zacząć od użycia wektora! Aby uzyskać więcej informacji, zobacz [Vector Class](../standard-library/vector-class.md).

Kontener ma niektóre siły `vector`, ale długość nie jest elastyczna. `array` Aby uzyskać więcej informacji, zobacz [Array Class](../standard-library/array-class-stl.md).

Kontener `deque` (kolejki z podwójną końcą) umożliwia szybkie Wstawianie i usuwanie na początku i na końcu kontenera. Współużytkuje dostęp swobodny i o `vector`elastycznej długości, ale nie jest ciągły. Aby uzyskać więcej informacji, zobacz [Klasa deque](../standard-library/deque-class.md).

`list` Kontener to połączona podwójna lista, która umożliwia dostęp dwukierunkowy, szybkie wstawienia i szybkie usuwanie w dowolnym miejscu kontenera, ale nie można losowo uzyskać dostępu do elementu w kontenerze. Aby uzyskać więcej informacji, zobacz [Klasa list](../standard-library/list-class.md).

Kontener jest pojedynczo połączoną listą — `list`wersją usługi do przodu. `forward_list` Aby uzyskać więcej informacji, zobacz [Klasa forward_list](../standard-library/forward-list-class.md).

## <a name="associative-containers"></a>Kontenery asocjacyjne

W kontenerach asocjacyjnych elementy są wstawiane we wstępnie zdefiniowanej kolejności — na przykład jako sortowane rosnąco. Dostępne są również nieuporządkowane Kontenery asocjacyjne. Kontenery asocjacyjne mogą być pogrupowane w dwa podzestawy: maps i zestawy.

A `map`, czasami określane jako słownik, składa się z pary klucz/wartość. Klucz służy do porządkowania sekwencji, a wartość jest skojarzona z tym kluczem. Na przykład `map` może zawierać klucze, które reprezentują każdy unikatowy wyraz w tekście i odpowiadające im wartości, które reprezentują liczbę razy, w których każdy wyraz pojawia się w tekście. Nieuporządkowana wersja programu `map` to `unordered_map`. Aby uzyskać więcej informacji, zobacz [Mapowanie klasy](../standard-library/map-class.md) i [klasy unordered_map](../standard-library/unordered-map-class.md).

`set` Jest to tylko rosnący kontener unikatowych elementów — wartość jest również kluczem. Nieuporządkowana wersja programu `set` to `unordered_set`. Aby uzyskać więcej informacji, zobacz [Ustawianie klasy](../standard-library/set-class.md) i [klasy unordered_set](../standard-library/unordered-set-class.md).

Oba `map` i`set` zezwalają na Wstawianie tylko jednego wystąpienia klucza lub elementu do kontenera. Jeśli jest wymaganych wiele wystąpień elementów, użyj `multimap` lub. `multiset` Nieuporządkowane wersje to `unordered_multimap` i `unordered_multiset`. Aby uzyskać więcej informacji, zobacz Klasa [multimap](../standard-library/multimap-class.md), Klasa [unordered_multimap](../standard-library/unordered-multimap-class.md), [Klasa wielokrotnego](../standard-library/multiset-class.md)użytku i [Klasa unordered_multiset](../standard-library/unordered-multiset-class.md).

Uporządkowane mapy i zestawy obsługują Iteratory dwukierunkowe, a ich nieuporządkowane odpowiedniki obsługują Iteratory do przodu. Aby uzyskać więcej informacji, [](../standard-library/iterators.md)zobacz Iteratory.

### <a name="heterogeneous-lookup-in-associative-containers-c14"></a>Wyszukiwanie heterogeniczne w kontenerach asocjacyjnych (C++ 14)

Uporządkowane Kontenery asocjacyjne (map, multimap, Set i zestaw wielokrotny) obsługują teraz niejednorodne wyszukiwanie, co oznacza, że nie jest już wymagane przekazanie dokładnie tego samego typu obiektu co klucz lub element w `find()` funkcjach składowych, takich jak i. `lower_bound()` . Zamiast tego można przekazać dowolny typ, dla którego zdefiniowano `operator<` przeciążoną wartość, która umożliwia porównanie z typem klucza.

Wyszukiwanie heterogenicznych jest włączane na podstawie zgody, jeśli podczas deklarowania zmiennej `std::less<>` kontenera `std::greater<>` określono lub "Diamond Funktor" komparator, jak pokazano poniżej:

```cpp
std::set<BigObject, std::less<>> myNewSet;
```

Jeśli używasz domyślnej komparator, kontener zachowuje się dokładnie tak, jak w C++ 11 i wcześniejszych.

W poniższym przykładzie pokazano, jak przeciążać `operator<` , aby umożliwić użytkownikom przeszukiwania, `std::set` po prostu przekazując małe ciągi, które można `BigObject::id` porównać z elementem członkowskim każdego obiektu.

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

Następujące funkcje członkowskie w mapowaniu, multimap, Set i zestaw wielokrotny są przeciążone, aby obsługiwały wyszukiwanie heterogeniczne:

1. find

1. count

1. lower_bound

1. upper_bound

1. equal_range

## <a name="container-adapters"></a>Karty kontenerów

Karta kontenera jest odmianą sekwencji lub kontenera asocjacyjnego, który ogranicza interfejs pod kątem prostoty i przejrzystości. Karty kontenerów nie obsługują iteratorów.

`queue` Kontener postępuje zgodnie z semantyką FIFO (pierwszy w, pierwszy z nich). Pierwszy element został wysunięty — to znaczy wstawiony do kolejki — jest pierwszy do *zdjęte*— czyli usunięty z kolejki. Aby uzyskać więcej informacji, zobacz [Kolejka klasy](../standard-library/queue-class.md).

`priority_queue` Kontener jest zorganizowany w taki sposób, że element, który ma najwyższą wartość, zawsze jest w kolejce. Aby uzyskać więcej informacji, zobacz [Klasa priority_queue](../standard-library/priority-queue-class.md).

`stack` Kontener postępuje zgodnie z następującą semantyką: LIFO (Ostatnia w, pierwsza z nich). Ostatni element wypchnięcia na stosie to pierwszy element zdjęte. Aby uzyskać więcej informacji, zobacz [Stack Class](../standard-library/stack-class.md).

Ponieważ karty kontenerów nie obsługują iteratorów, nie mogą być używane z algorytmami C++ standardowej biblioteki. Aby uzyskać więcej informacji, [](../standard-library/algorithms.md)Zobacz algorytmy.

## <a name="requirements-for-container-elements"></a>Wymagania dotyczące elementów kontenera

Ogólnie rzecz biorąc, elementy wstawiane C++ do kontenera biblioteki standardowej mogą być tylko obiektami dowolnego typu, jeśli są one możliwe do kopiowania. Elementy tylko przenośne — na przykład te `vector<unique_ptr<T>>` , które są tworzone za pomocą programu `unique_ptr<>` , będą działać tak długo, jak nie są wywoływane funkcje członkowskie, które próbują je skopiować.

Destruktor nie może zgłosić wyjątku.

Uporządkowane Kontenery asocjacyjne — opisane wcześniej w tym artykule — muszą mieć zdefiniowany publiczny operator porównania. (Domyślnie operator jest `operator<`, ale nawet typy, które nie działają z `operator<` są obsługiwane.

Niektóre operacje na kontenerach mogą również wymagać publicznego konstruktora domyślnego i publicznego operatora równoważności. Na przykład nieuporządkowane Kontenery asocjacyjne wymagają obsługi równości i wyznaczania wartości skrótu.

## <a name="accessing-container-elements"></a>Dostęp do elementów kontenera

Do elementów kontenera uzyskuje się dostęp przy użyciu iteratorów. Aby uzyskać więcej informacji, [](../standard-library/iterators.md)zobacz Iteratory.

> [!NOTE]
> Możesz również użyć [dla pętli](../cpp/range-based-for-statement-cpp.md) do iteracji dla C++ standardowych kolekcji bibliotek.

## <a name="comparing-containers"></a>Porównywanie kontenerów

Wszystkie kontenery przeciążą operator = = do porównywania dwóch kontenerów tego samego typu, które mają ten sam typ elementu. Można użyć = =,\<aby porównać ciąg wektora > do innego > wektora\<, ale nie można użyć go do porównania ciągu wektora\<> z > ciągu\<listy lub ciągiem wektora\<> do wektora \<char * >.  W języku C++ 98/03 można użyć [wartości std:: EQUAL](algorithm-functions.md#equal) lub [std:: niezgodność](algorithm-functions.md#mismatch) do porównywania niepodobnych typów kontenerów i/lub typów elementów. W języku C++ 11 można również użyć [std:: is_permutation](algorithm-functions.md#is_permutation). Jednak we wszystkich przypadkach funkcja przyjmuje, że kontenery są takie same. Jeśli drugi zakres jest krótszy niż pierwszy, wówczas wyniki niezdefiniowanego zachowania. Jeśli drugi zakres jest dłuższy, wyniki nadal mogą być nieprawidłowe, ponieważ porównanie nigdy nie przechodzi poza koniec pierwszego zakresu.

### <a name="comparing-dissimilar-containers-c14"></a>Porównywanie niepodobnych kontenerów (C++ 14)

W języku c++ 14 i nowszych można porównać niepodobne kontenery i/lub inne typy elementów przy użyciu jednego z `std::equal`przeciążeń `std::mismatch` `std::is_permutation` funkcji, które mają dwa kompletne zakresy. Te przeciążenia umożliwiają porównywanie kontenerów z różnymi długościami. Te przeciążenia są znacznie mniej podatne na błędy użytkownika i są zoptymalizowane pod kątem zwrócenia fałszywych wartości w czasie, gdy są porównywane kontenery o niepodobnej długości. Z tego względu zalecamy korzystanie z tych przeciążeń, chyba że (1) masz bardzo oczywisty powód nie dotyczy, lub (2) używasz kontenera [std:: list](../standard-library/list-class.md) , który nie korzysta z optymalizacji podwójnego zakresu.

## <a name="see-also"></a>Zobacz także

[Opakowania](../cpp/containers-modern-cpp.md)\
[C++Dokumentacja biblioteki standardowej](../standard-library/cpp-standard-library-reference.md)\
[\<Przykładowy > kontenera](../standard-library/sample-container.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
