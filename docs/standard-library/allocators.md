---
title: Allocators
ms.date: 11/04/2016
helpviewer_keywords:
- allocators
- C++ Standard Library, allocators
ms.assetid: ac95023b-9e7d-49f5-861a-bf7a9a340746
ms.openlocfilehash: cb1b0e0d1466d4af5ba255bdf3d00b11cd921fd6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457547"
---
# <a name="allocators"></a>Allocators

Przypisania są używane przez bibliotekę C++ Standard do obsługi alokacji i cofania przydziału elementów przechowywanych w kontenerach. Wszystkie C++ Kontenery biblioteki standardowej z wyjątkiem std:: Array mają parametr szablonu typu `allocator<Type>`, gdzie `Type` reprezentuje typ elementu kontenera. Na przykład Klasa Vector jest zadeklarowana w następujący sposób:

```cpp
template <
    class Type,
    class Allocator = allocator<Type>
>
class vector
```

C++ Standardowa biblioteka zawiera domyślną implementację alokatora. W języku C++ 11 i nowszych domyślny Alokator został zaktualizowany w celu uwidocznienia mniejszych interfejsów; Nowy Alokator jest nazywany minimalnym *alokatorem*. W szczególności `construct()` element członkowski minimalnego alokatora obsługuje semantykę przenoszenia, co może znacznie poprawić wydajność. W większości przypadków ten domyślny Alokator powinien być wystarczający. W języku c++ 11 wszystkie standardowe typy biblioteki i funkcje, które przyjmują parametr typu alokatora, obsługują minimalny interfejs alokatora `shared_ptr, allocate_shared()`, w `basic_string`tym `std::function`, i.  Aby uzyskać więcej informacji na temat domyślnego alokatora, zobacz [Klasa alokatora](../standard-library/allocator-class.md).

## <a name="writing-your-own-allocator-c11"></a>Pisanie własnego alokatora (C++ 11)

Domyślny Alokator używa **nowych** i usunięć do przydzielania i **cofania** alokacji pamięci. Jeśli chcesz użyć innej metody alokacji pamięci, takiej jak użycie pamięci współużytkowanej, należy utworzyć własny Alokator. Jeśli jest przeznaczony dla języka C++ 11 i musisz napisać nowy Alokator niestandardowy, jeśli to możliwe, należy wprowadzić minimalny Alokator. Nawet jeśli już zaimplementowano alokatora w starym stylu, Rozważ zmodyfikowanie go jako *minimalnego alokatora* , aby skorzystać z bardziej wydajnej `construct()` metody, która zostanie udostępniona automatycznie.

Minimalny Alokator wymaga znacznie mniej typowego i umożliwia skoncentrowanie się na `allocate` `deallocate` funkcjach składowych, które wykonują wszystkie prace. Podczas tworzenia minimalnego alokatora nie należy wdrażać żadnych elementów członkowskich z wyjątkiem tych, które przedstawiono w poniższym przykładzie:

1. Konwertowanie konstruktora kopiującego (Zobacz przykład)

1. operator==

1. operator!=

1. allocate

1. alokowany

Domyślny `construct()` element członkowski języka c++ 11, który zostanie udostępniony dla Ciebie jest idealnym przekazywaniem i umożliwia semantykę przenoszenia, jest znacznie bardziej wydajny w wielu przypadkach niż w przypadku starszej wersji.

> [!WARNING]
> W czasie kompilacji C++ standardowa biblioteka używa klasy allocator_traits w celu wykrywania, które elementy członkowskie zostały podane jawnie i udostępniają domyślną implementację dla nieobecnych elementów członkowskich. Nie zakłócaj tego mechanizmu, dostarczając specjalizację allocator_traits dla Twojego alokatora.

W poniższym przykładzie pokazano minimalną implementację alokatora, który `malloc` używa `free`i. Zwróć uwagę na użycie nowego typu `std::bad_array_new_length` wyjątku, który jest zgłaszany, jeśli rozmiar tablicy jest mniejszy niż zero lub większy niż maksymalny dozwolony rozmiar.

```cpp
#pragma once
#include <stdlib.h> //size_t, malloc, free
#include <new> // bad_alloc, bad_array_new_length
#include <memory>
template <class T>
struct Mallocator
{
    typedef T value_type;
    Mallocator() noexcept {} //default ctor not required by C++ Standard Library

    // A converting copy constructor:
    template<class U> Mallocator(const Mallocator<U>&) noexcept {}
    template<class U> bool operator==(const Mallocator<U>&) const noexcept
    {
        return true;
    }
    template<class U> bool operator!=(const Mallocator<U>&) const noexcept
    {
        return false;
    }
    T* allocate(const size_t n) const;
    void deallocate(T* const p, size_t) const noexcept;
};

template <class T>
T* Mallocator<T>::allocate(const size_t n) const
{
    if (n == 0)
    {
        return nullptr;
    }
    if (n > static_cast<size_t>(-1) / sizeof(T))
    {
        throw std::bad_array_new_length();
    }
    void* const pv = malloc(n * sizeof(T));
    if (!pv) { throw std::bad_alloc(); }
    return static_cast<T*>(pv);
}

template<class T>
void Mallocator<T>::deallocate(T * const p, size_t) const noexcept
{
    free(p);
}
```

## <a name="writing-your-own-allocator-c03"></a>Pisanie własnego alokatora (C++ 03)

W języku C++ 03 każdy Alokator używany z C++ kontenerami biblioteki standardowej musi implementować następujące definicje typów:

|||
|-|-|
|`const_pointer`|`rebind`|
|`const_reference`|`reference`|
|`difference_type`|`size_type`|
|`pointer`|`value_type`|

Ponadto każdy Alokator używany z C++ kontenerami biblioteki standardowej musi implementować następujące metody:

|||
|-|-|
|Konstruktor|`deallocate`|
|Konstruktor kopiujący|`destroy`|
|Destruktor|`max_size`|
|`address`|`operator==`|
|`allocate`|`operator!=`|
|`construct`||

Aby uzyskać więcej informacji na temat tych definicji typów i metod, zobacz [Klasa alokatora](../standard-library/allocator-class.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
