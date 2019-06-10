---
title: 'Instrukcje: Tworzenie wystąpień shared_ptr i korzystanie'
ms.custom: how-to
ms.date: 05/22/2019
ms.topic: conceptual
ms.assetid: 7d6ebb73-fa0d-4b0b-a528-bf05de96518e
ms.openlocfilehash: ac6db74122383ef8adb0f208860a6f6fba02dcc7
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821682"
---
# <a name="how-to-create-and-use-sharedptr-instances"></a>Instrukcje: Tworzenie wystąpień shared_ptr i korzystanie

Typ `shared_ptr` jest inteligentnym wskaźnikiem w standardowej bibliotece języka C++ przeznaczonym dla scenariuszy, w których więcej niż jeden właściciel może być zmuszony do zarządzania okresem istnienia obiektu w pamięci. Po zainicjowaniu wskaźnika `shared_ptr` można go kopiować, przekazywać wg wartości w argumentach funkcji oraz przypisywać do innych wystąpień wskaźnika `shared_ptr`. Wszystkie wystąpienia wskazują ten sam obiekt oraz mają wspólny dostęp do jednego „bloku sterującego”, który zwiększa i zmniejsza liczbę odwołań po każdym dodaniu nowego wskaźnika `shared_ptr`, wykroczeniu przez wskaźnik poza zakres lub jego zresetowaniu. Gdy licznik odwołań osiągnie zero, blok sterujący usuwa zasób pamięci i samego siebie.

Na ilustracji poniżej widać kilka wystąpień wskaźnika `shared_ptr`, które wskazują jedną lokalizację w pamięci.

![Diagram wskaźnika współdzielona](../cpp/media/shared_ptr.png "Shared wskaźnika diagramu")

## <a name="example-setup"></a>Konfiguracja przykładu

Przykłady, które należy wykonać wszystkie założono, że został uwzględniony w nagłówkach wymagane i zadeklarowana wymaganych typów, jak pokazano poniżej:

```cpp
// shared_ptr-examples.cpp
// The following examples assume these declarations:
#include <algorithm>
#include <iostream>
#include <memory>
#include <string>
#include <vector>

struct MediaAsset
{
    virtual ~MediaAsset() = default; // make it polymorphic
};

struct Song : public MediaAsset
{
    std::wstring artist;
    std::wstring title;
    Song(const std::wstring& artist_, const std::wstring& title_) :
        artist{ artist_ }, title{ title_ } {}
};

struct Photo : public MediaAsset
{
    std::wstring date;
    std::wstring location;
    std::wstring subject;
    Photo(
        const std::wstring& date_,
        const std::wstring& location_,
        const std::wstring& subject_) :
        date{ date_ }, location{ location_ }, subject{ subject_ } {}
};

using namespace std;

int main()
{
    // The examples go here, in order:
    // Example 1
    // Example 2
    // Example 3
    // Example 4
    // Example 6
}
```

## <a name="example-1"></a>Przykład 1

Możliwe, używaj [make_shared](../standard-library/memory-functions.md#make_shared) funkcji, aby utworzyć `shared_ptr` podczas tworzenia zasobu pamięci po raz pierwszy. Funkcja `make_shared` jest bezpieczna pod względem wyjątków. Wykorzystuje to samo wywołanie, aby przydzielić pamięci dla bloku sterowania i zasobów, co zmniejsza koszty tworzenia. Jeśli nie używasz `make_shared`, musisz użyć jawnego `new` wyrażenia do utworzenia obiektu, następnie przekazać go do `shared_ptr` konstruktora. Poniższy przykład pokazuje różne sposoby deklarowania i inicjowania wskaźnika `shared_ptr` razem z nowym obiektem.

[!code-cpp[stl_smart_pointers#1](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_1.cpp)]

## <a name="example-2"></a>Przykład 2

W przykładzie poniżej pokazano sposób deklarowania i inicjowania wystąpień wskaźnika `shared_ptr`, które przyjmują współwłasność obiektu przydzielonego wcześniej przez inny wskaźnik `shared_ptr`. Załóżmy, że zainicjowanym wskaźnikiem `sp2` jest `shared_ptr`.

[!code-cpp[stl_smart_pointers#2](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_2.cpp)]

## <a name="example-3"></a>Przykład 3

`shared_ptr` jest także przydatny w C++ kontenery standardowej biblioteki, gdy są używane algorytmy kopiujące elementy. We wskaźniku `shared_ptr` można opakować elementy, po czym skopiować go do innych kontenerów przy założeniu, że bazowa pamięć jest zajęta tylko przez niezbędny czas, nie dłużej. Poniższy przykład pokazuje, jak używać algorytmu `replace_copy_if` do wystąpień wskaźnika `shared_ptr` w wektorze.

[!code-cpp[stl_smart_pointers#4](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_3.cpp)]

## <a name="example-4"></a>Przykład 4

Za pomocą funkcji `dynamic_pointer_cast`, `static_pointer_cast` i `const_pointer_cast` można rzutować wskaźnik `shared_ptr`. Funkcje te przypominają operatory `dynamic_cast`, `static_cast` i `const_cast`. W przykładzie poniżej pokazano, jak przetestować typ pochodny każdego elementu w wektorze wskaźnika `shared_ptr` klas bazowych, a następnie skopiować elementy i wyświetlić o nich informacje.

[!code-cpp[stl_smart_pointers#5](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_4.cpp)]

## <a name="example-5"></a>Przykład 5

Wskaźnik `shared_ptr` można przekazać do innej funkcji w następujące sposoby:

- Przekazanie wskaźnika `shared_ptr` wg wartości. Powoduje to wywołanie konstruktora kopiującego, zwiększenie wartości licznika odwołań i przekazanie własności obiektowi wywoływanemu. Brak niewielkiej ilości obciążenia, w tej operacji, które mogą być istotne w zależności od tego, ile `shared_ptr` obiektów, przechodząc. Użyj tej opcji, gdy kontrakt kodu niejawny lub jawny między obiektami wywołującym i wywoływanym wymaga, że obiekt wywoływany był właścicielem.

- Przekazanie wskaźnika `shared_ptr` wg odwołania lub odwołania stałego. W tym przypadku zwiększany nie jest licznik odwołań, a obiekt wywoływany ma dostęp do wskaźnika tak długo, jak długo obiekt wywołujący nie wykraczają poza zakres. Alternatywnie obiekt wywoływany może wybrać, aby utworzyć `shared_ptr` na podstawie odwołania i stać się współwłaścicielem. Opcji należy używać w sytuacjach, gdy obiekt wywołujący nic nie wie o obiekcie wywoływanym albo kiedy trzeba przekazać wskaźnik `shared_ptr`, ale ze względów wydajnościowych operacje kopiowania są niepożądane.

- Przekazanie bazowego wskaźnika lub odwołania do bazowego obiektu. Włącza / / wywoływany użyć obiektu, ale nie umożliwiają współwłaścicielem ani wydłużać jego okresu istnienia. Jeśli obiekt wywoływany tworzy `shared_ptr` ze surowego wskaźnika, nowy `shared_ptr` jest niezależny od oryginału i nie steruje bazowym zasobem. Opcję należy stosować w przypadku, gdy kontrakt między obiektami wywołującym i wywoływanym jednoznacznie określa, że obiekt wywołujący zachowuje własność nad okresem istnienia wskaźnika `shared_ptr`.

- Podczas wybierania sposób przekazywania `shared_ptr`, określić, czy obiekt wywoływany ma być współwłaścicielem bazowego zasobu. „Właściciel” to obiekt lub funkcja, która może utrzymywać istnienie bazowego zasobu tak długo, jak to konieczne. Jeśli obiekt wywołujący ma gwarantować, że obiekt wywoływany może przedłużać okres istnienia wskaźnika poza okres istnienia funkcji, należy użyć pierwszej opcji. Gdy przedłużanie okresu istnienia przez obiekt wywoływany nie ma znaczenia, należy stosować przekazywanie wg odwołania i pozwolić obiektowi wywoływanemu na opcjonalne kopiowanie wskaźnika.

- Jeśli musisz przyznać dostęp do funkcji pomocnika do bazowego wskaźnika, a wiadomo, funkcja pomocnika będzie po prostu użyj wskaźnika i zwróci wartość przed zwróceniem wywoływania zwraca funkcję, a następnie tej funkcji nie ma być współwłaścicielem bazowego wskaźnika. Potrzebuje tylko dostępu do wskaźnika w trakcie okresu istnienia obiektu wywołującego wskaźnika `shared_ptr`. W tym przypadku są bezpiecznie przekazać `shared_ptr` wg odwołania albo przekazać surowego wskaźnika lub odwołania do bazowego obiektu. Taki sposób przekazania jest nieco korzystniejszy pod względem obciążenia systemu, a dodatkowo może pomóc lepiej wyrazić cele programistyczne.

- Czasami, na przykład w konstrukcji `std::vector<shared_ptr<T>>`, może być konieczne przekazanie każdego wskaźnika `shared_ptr` do treści wyrażenia lambda lub do nazwanego obiektu funkcji. Jeśli wyrażenie lambda lub funkcja nie przechowuje wskaźnika, należy przekazać `shared_ptr` przez odwołanie, aby uniknąć wywoływania konstruktora kopiującego dla każdego elementu.

## <a name="example-6"></a>Przykład 6

W przykładzie poniżej pokazano, jak wskaźnik `shared_ptr` przeciąża różne operatory porównania, aby umożliwić porównywanie wskaźników w pamięci, której właścicielami są wystąpienia wskaźnika `shared_ptr`.

[!code-cpp[stl_smart_pointers#3](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_6.cpp)]

## <a name="see-also"></a>Zobacz także

[Wskaźniki inteligentne (Modern C++)](../cpp/smart-pointers-modern-cpp.md)
