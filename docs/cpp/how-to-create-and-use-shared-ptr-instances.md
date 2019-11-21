---
title: 'How to: Create and use shared_ptr instances'
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 7d6ebb73-fa0d-4b0b-a528-bf05de96518e
ms.openlocfilehash: 9820e4cd2d1b981d82760fc1cea4e07c85792177
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245830"
---
# <a name="how-to-create-and-use-shared_ptr-instances"></a>How to: Create and Use shared_ptr instances

Typ `shared_ptr` jest inteligentnym wskaźnikiem w standardowej bibliotece języka C++ przeznaczonym dla scenariuszy, w których więcej niż jeden właściciel może być zmuszony do zarządzania okresem istnienia obiektu w pamięci. Po zainicjowaniu wskaźnika `shared_ptr` można go kopiować, przekazywać wg wartości w argumentach funkcji oraz przypisywać do innych wystąpień wskaźnika `shared_ptr`. Wszystkie wystąpienia wskazują ten sam obiekt oraz mają wspólny dostęp do jednego „bloku sterującego”, który zwiększa i zmniejsza liczbę odwołań po każdym dodaniu nowego wskaźnika `shared_ptr`, wykroczeniu przez wskaźnik poza zakres lub jego zresetowaniu. Gdy licznik odwołań osiągnie zero, blok sterujący usuwa zasób pamięci i samego siebie.

Na ilustracji poniżej widać kilka wystąpień wskaźnika `shared_ptr`, które wskazują jedną lokalizację w pamięci.

![Shared pointer diagram](media/shared_ptr.png "Shared pointer diagram")

## <a name="example-setup"></a>Example setup

The examples that follow all assume that you've included the required headers and declared the required types, as shown here:

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

Whenever possible, use the [make_shared](../standard-library/memory-functions.md#make_shared) function to create a `shared_ptr` when the memory resource is created for the first time. Funkcja `make_shared` jest bezpieczna pod względem wyjątków. It uses the same call to allocate the memory for the control block and the resource, which reduces the construction overhead. If you don't use `make_shared`, then you have to use an explicit `new` expression to create the object before you pass it to the `shared_ptr` constructor. Poniższy przykład pokazuje różne sposoby deklarowania i inicjowania wskaźnika `shared_ptr` razem z nowym obiektem.

[!code-cpp[stl_smart_pointers#1](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_1.cpp)]

## <a name="example-2"></a>Example 2

W przykładzie poniżej pokazano sposób deklarowania i inicjowania wystąpień wskaźnika `shared_ptr`, które przyjmują współwłasność obiektu przydzielonego wcześniej przez inny wskaźnik `shared_ptr`. Załóżmy, że zainicjowanym wskaźnikiem `sp2` jest `shared_ptr`.

[!code-cpp[stl_smart_pointers#2](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_2.cpp)]

## <a name="example-3"></a>Example 3

`shared_ptr` is also helpful in C++ Standard Library containers when you're using algorithms that copy elements. We wskaźniku `shared_ptr` można opakować elementy, po czym skopiować go do innych kontenerów przy założeniu, że bazowa pamięć jest zajęta tylko przez niezbędny czas, nie dłużej. Poniższy przykład pokazuje, jak używać algorytmu `remove_copy_if` do wystąpień wskaźnika `shared_ptr` w wektorze.

[!code-cpp[stl_smart_pointers#4](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_3.cpp)]

## <a name="example-4"></a>Example 4

Za pomocą funkcji `dynamic_pointer_cast`, `static_pointer_cast` i `const_pointer_cast` można rzutować wskaźnik `shared_ptr`. Funkcje te przypominają operatory `dynamic_cast`, `static_cast` i `const_cast`. W przykładzie poniżej pokazano, jak przetestować typ pochodny każdego elementu w wektorze wskaźnika `shared_ptr` klas bazowych, a następnie skopiować elementy i wyświetlić o nich informacje.

[!code-cpp[stl_smart_pointers#5](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_4.cpp)]

## <a name="example-5"></a>Example 5

Wskaźnik `shared_ptr` można przekazać do innej funkcji w następujące sposoby:

- Przekazanie wskaźnika `shared_ptr` wg wartości. Powoduje to wywołanie konstruktora kopiującego, zwiększenie wartości licznika odwołań i przekazanie własności obiektowi wywoływanemu. There's a small amount of overhead in this operation, which may be significant depending on how many `shared_ptr` objects you're passing. Use this option when the implied or explicit code contract between the caller and callee requires that the callee be an owner.

- Przekazanie wskaźnika `shared_ptr` wg odwołania lub odwołania stałego. In this case, the reference count isn't incremented, and the callee can access the pointer as long as the caller doesn't go out of scope. Or, the callee can decide to create a `shared_ptr` based on the reference, and become a shared owner. Opcji należy używać w sytuacjach, gdy obiekt wywołujący nic nie wie o obiekcie wywoływanym albo kiedy trzeba przekazać wskaźnik `shared_ptr`, ale ze względów wydajnościowych operacje kopiowania są niepożądane.

- Przekazanie bazowego wskaźnika lub odwołania do bazowego obiektu. This enables the callee to use the object, but doesn't enable it to share ownership or extend the lifetime. If the callee creates a `shared_ptr` from the raw pointer, the new `shared_ptr` is independent from the original, and doesn't control the underlying resource. Opcję należy stosować w przypadku, gdy kontrakt między obiektami wywołującym i wywoływanym jednoznacznie określa, że obiekt wywołujący zachowuje własność nad okresem istnienia wskaźnika `shared_ptr`.

- When you're deciding how to pass a `shared_ptr`, determine whether the callee has to share ownership of the underlying resource. „Właściciel” to obiekt lub funkcja, która może utrzymywać istnienie bazowego zasobu tak długo, jak to konieczne. Jeśli obiekt wywołujący ma gwarantować, że obiekt wywoływany może przedłużać okres istnienia wskaźnika poza okres istnienia funkcji, należy użyć pierwszej opcji. Gdy przedłużanie okresu istnienia przez obiekt wywoływany nie ma znaczenia, należy stosować przekazywanie wg odwołania i pozwolić obiektowi wywoływanemu na opcjonalne kopiowanie wskaźnika.

- If you have to give a helper function access to the underlying pointer, and you know that the helper function will just use the pointer and return before the calling function returns, then that function doesn't have to share ownership of the underlying pointer. Potrzebuje tylko dostępu do wskaźnika w trakcie okresu istnienia obiektu wywołującego wskaźnika `shared_ptr`. In this case, it's safe to pass the `shared_ptr` by reference, or pass the raw pointer or a reference to the underlying object. Taki sposób przekazania jest nieco korzystniejszy pod względem obciążenia systemu, a dodatkowo może pomóc lepiej wyrazić cele programistyczne.

- Czasami, na przykład w konstrukcji `std::vector<shared_ptr<T>>`, może być konieczne przekazanie każdego wskaźnika `shared_ptr` do treści wyrażenia lambda lub do nazwanego obiektu funkcji. If the lambda or function doesn't store the pointer, then pass the `shared_ptr` by reference to avoid invoking the copy constructor for each element.

## <a name="example-6"></a>Example 6

W przykładzie poniżej pokazano, jak wskaźnik `shared_ptr` przeciąża różne operatory porównania, aby umożliwić porównywanie wskaźników w pamięci, której właścicielami są wystąpienia wskaźnika `shared_ptr`.

[!code-cpp[stl_smart_pointers#3](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_6.cpp)]

## <a name="see-also"></a>Zobacz także

[Wskaźniki inteligentne (Modern C++)](smart-pointers-modern-cpp.md)
