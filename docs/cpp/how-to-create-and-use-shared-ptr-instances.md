---
title: 'Instrukcje: Tworzenie wystąpień shared_ptr i korzystanie z nich'
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 7d6ebb73-fa0d-4b0b-a528-bf05de96518e
ms.openlocfilehash: 44d375f72cf409df1e67b72dd76e196051dacf93
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87187962"
---
# <a name="how-to-create-and-use-shared_ptr-instances"></a>Instrukcje: Tworzenie wystąpień shared_ptr i korzystanie z nich

Typ `shared_ptr` jest inteligentnym wskaźnikiem w standardowej bibliotece języka C++ przeznaczonym dla scenariuszy, w których więcej niż jeden właściciel może być zmuszony do zarządzania okresem istnienia obiektu w pamięci. Po zainicjowaniu wskaźnika `shared_ptr` można go kopiować, przekazywać wg wartości w argumentach funkcji oraz przypisywać do innych wystąpień wskaźnika `shared_ptr`. Wszystkie wystąpienia wskazują ten sam obiekt oraz mają wspólny dostęp do jednego „bloku sterującego”, który zwiększa i zmniejsza liczbę odwołań po każdym dodaniu nowego wskaźnika `shared_ptr`, wykroczeniu przez wskaźnik poza zakres lub jego zresetowaniu. Gdy licznik odwołań osiągnie zero, blok sterujący usuwa zasób pamięci i samego siebie.

Na ilustracji poniżej widać kilka wystąpień wskaźnika `shared_ptr`, które wskazują jedną lokalizację w pamięci.

![Udostępniony diagram wskaźników](media/shared_ptr.png "Udostępniony diagram wskaźników")

## <a name="example-setup"></a>Przykładowa konfiguracja

Poniższe przykłady założono, że zostały dołączone wymagane nagłówki i zadeklarowano wymagane typy, jak pokazano poniżej:

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

Jeśli jest to możliwe, użyj funkcji [make_shared](../standard-library/memory-functions.md#make_shared) , aby utworzyć `shared_ptr` gdy zasób pamięci jest tworzony po raz pierwszy. Funkcja `make_shared` jest bezpieczna pod względem wyjątków. Używa tego samego wywołania do przydzielania pamięci dla bloku sterowania i zasobu, co zmniejsza obciążenie związane z konstruowaniem. Jeśli nie używasz `make_shared` , musisz użyć jawnego **`new`** wyrażenia, aby utworzyć obiekt przed przekazaniem go do `shared_ptr` konstruktora. Poniższy przykład pokazuje różne sposoby deklarowania i inicjowania wskaźnika `shared_ptr` razem z nowym obiektem.

[!code-cpp[stl_smart_pointers#1](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_1.cpp)]

## <a name="example-2"></a>Przykład 2

W przykładzie poniżej pokazano sposób deklarowania i inicjowania wystąpień wskaźnika `shared_ptr`, które przyjmują współwłasność obiektu przydzielonego wcześniej przez inny wskaźnik `shared_ptr`. Załóżmy, że zainicjowanym wskaźnikiem `sp2` jest `shared_ptr`.

[!code-cpp[stl_smart_pointers#2](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_2.cpp)]

## <a name="example-3"></a>Przykład 3

`shared_ptr`jest również przydatne w kontenerach standardowej biblioteki języka C++, gdy używane są algorytmy kopiujące elementy. We wskaźniku `shared_ptr` można opakować elementy, po czym skopiować go do innych kontenerów przy założeniu, że bazowa pamięć jest zajęta tylko przez niezbędny czas, nie dłużej. Poniższy przykład pokazuje, jak używać algorytmu `remove_copy_if` do wystąpień wskaźnika `shared_ptr` w wektorze.

[!code-cpp[stl_smart_pointers#4](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_3.cpp)]

## <a name="example-4"></a>Przykład 4

Za pomocą funkcji `dynamic_pointer_cast`, `static_pointer_cast` i `const_pointer_cast` można rzutować wskaźnik `shared_ptr`. Funkcje te przypominają **`dynamic_cast`** operatory, **`static_cast`** i **`const_cast`** . W przykładzie poniżej pokazano, jak przetestować typ pochodny każdego elementu w wektorze wskaźnika `shared_ptr` klas bazowych, a następnie skopiować elementy i wyświetlić o nich informacje.

[!code-cpp[stl_smart_pointers#5](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_4.cpp)]

## <a name="example-5"></a>Przykład 5

Wskaźnik `shared_ptr` można przekazać do innej funkcji w następujące sposoby:

- Przekazanie wskaźnika `shared_ptr` wg wartości. Powoduje to wywołanie konstruktora kopiującego, zwiększenie wartości licznika odwołań i przekazanie własności obiektowi wywoływanemu. W tej operacji występuje niewielka część kosztów, która może być istotna w zależności od liczby przekazywanych `shared_ptr` obiektów. Użyj tej opcji, gdy implikowany lub jawny kontrakt kodu między obiektem wywołującym i wywoływanym wymaga, aby element wywoływany był właścicielem.

- Przekazanie wskaźnika `shared_ptr` wg odwołania lub odwołania stałego. W tym przypadku licznik odwołań nie jest zwiększany, a wywoływany może uzyskać dostęp do wskaźnika, o ile obiekt wywołujący nie wykracza poza zakres. Lub element wywoływany może zdecydować się na utworzenie na `shared_ptr` podstawie odwołania i udostępnienie właściciela. Opcji należy używać w sytuacjach, gdy obiekt wywołujący nic nie wie o obiekcie wywoływanym albo kiedy trzeba przekazać wskaźnik `shared_ptr`, ale ze względów wydajnościowych operacje kopiowania są niepożądane.

- Przekazanie bazowego wskaźnika lub odwołania do bazowego obiektu. Dzięki temu obiekt wywoływany może korzystać z obiektu, ale nie pozwala na udostępnianie własności ani zwiększenie okresu istnienia. Jeśli obiekt wywoływany tworzy `shared_ptr` ze wskaźnika pierwotnego, nowy `shared_ptr` jest niezależny od oryginału i nie kontroluje bazowego zasobu. Opcję należy stosować w przypadku, gdy kontrakt między obiektami wywołującym i wywoływanym jednoznacznie określa, że obiekt wywołujący zachowuje własność nad okresem istnienia wskaźnika `shared_ptr`.

- Podczas decydowania o sposobie przekazywania `shared_ptr` należy określić, czy element wywoływany ma udostępniać własność bazowego zasobu. „Właściciel” to obiekt lub funkcja, która może utrzymywać istnienie bazowego zasobu tak długo, jak to konieczne. Jeśli obiekt wywołujący ma gwarantować, że obiekt wywoływany może przedłużać okres istnienia wskaźnika poza okres istnienia funkcji, należy użyć pierwszej opcji. Gdy przedłużanie okresu istnienia przez obiekt wywoływany nie ma znaczenia, należy stosować przekazywanie wg odwołania i pozwolić obiektowi wywoływanemu na opcjonalne kopiowanie wskaźnika.

- Jeśli konieczne jest przyznanie funkcji pomocnika dostępu do podstawowego wskaźnika i wiadomo, że funkcja pomocnika będzie używać wskaźnika i zwracać przed wywołaniem funkcji, wówczas ta funkcja nie musi udostępniać własności bazowego wskaźnika. Potrzebuje tylko dostępu do wskaźnika w trakcie okresu istnienia obiektu wywołującego wskaźnika `shared_ptr`. W takim przypadku jest bezpieczne przekazywanie `shared_ptr` przez odwołanie lub przekazanie surowego wskaźnika lub odwołania do obiektu źródłowego. Taki sposób przekazania jest nieco korzystniejszy pod względem obciążenia systemu, a dodatkowo może pomóc lepiej wyrazić cele programistyczne.

- Czasami, na przykład w konstrukcji `std::vector<shared_ptr<T>>`, może być konieczne przekazanie każdego wskaźnika `shared_ptr` do treści wyrażenia lambda lub do nazwanego obiektu funkcji. Jeśli wyrażenie lambda lub funkcja nie przechowuje wskaźnika, Przekaż `shared_ptr` przez odwołanie, aby uniknąć wywoływania konstruktora kopiującego dla każdego elementu.

## <a name="example-6"></a>Przykład 6

W przykładzie poniżej pokazano, jak wskaźnik `shared_ptr` przeciąża różne operatory porównania, aby umożliwić porównywanie wskaźników w pamięci, której właścicielami są wystąpienia wskaźnika `shared_ptr`.

[!code-cpp[stl_smart_pointers#3](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_6.cpp)]

## <a name="see-also"></a>Zobacz także

[Inteligentne wskaźniki (nowoczesne C++)](smart-pointers-modern-cpp.md)
