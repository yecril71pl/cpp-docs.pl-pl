---
title: Allocators
ms.date: 11/04/2016
helpviewer_keywords:
- allocators
- C++ Standard Library, allocators
ms.assetid: ac95023b-9e7d-49f5-861a-bf7a9a340746
ms.openlocfilehash: abef6f4e641b7936157ee063443a5b2a220fdd52
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623513"
---
# <a name="allocators"></a>Allocators

Przypisania są używane przez standardową bibliotekę języka C++ do obsługi alokacji i cofania przydziału elementów przechowywanych w kontenerach. Wszystkie kontenery standardowej biblioteki C++, z wyjątkiem std:: Array, mają parametr szablonu typu `allocator<Type>` , gdzie `Type` reprezentuje typ elementu kontenera. Na przykład Klasa Vector jest zadeklarowana w następujący sposób:

```cpp
template <
    class Type,
    class Allocator = allocator<Type>
>
class vector
```

Standardowa biblioteka języka C++ zawiera domyślną implementację alokatora. W języku C++ 11 i nowszych domyślny Alokator został zaktualizowany w celu uwidocznienia mniejszych interfejsów; Nowy Alokator jest nazywany *minimalnym alokatorem*. W szczególności element członkowski minimalnego alokatora `construct()` obsługuje semantykę przenoszenia, co może znacznie poprawić wydajność. W większości przypadków ten domyślny Alokator powinien być wystarczający. W języku C++ 11 wszystkie standardowe typy biblioteki i funkcje, które przyjmują parametr typu alokatora, obsługują minimalny interfejs alokatora, w tym `std::function` , `shared_ptr, allocate_shared()` i `basic_string` .  Aby uzyskać więcej informacji na temat domyślnego alokatora, zobacz [Klasa alokatora](allocator-class.md).

## <a name="writing-your-own-allocator-c11"></a>Pisanie własnego alokatora (C++ 11)

Domyślny Alokator używa **nowych** i usunięć do przydzielania i **cofania** alokacji pamięci. Jeśli chcesz użyć innej metody alokacji pamięci, takiej jak użycie pamięci współużytkowanej, należy utworzyć własny Alokator. Jeśli jest przeznaczony dla języka C++ 11 i musisz napisać nowy Alokator niestandardowy, jeśli to możliwe, należy wprowadzić minimalny Alokator. Nawet jeśli już zaimplementowano alokatora w starym stylu, Rozważ zmodyfikowanie go jako *minimalnego alokatora* , aby skorzystać z bardziej wydajnej `construct()` metody, która zostanie udostępniona automatycznie.

Minimalny Alokator wymaga znacznie mniej typowego i umożliwia skoncentrowanie się na `allocate` `deallocate` funkcjach składowych, które wykonują wszystkie prace. Podczas tworzenia minimalnego alokatora nie należy wdrażać żadnych elementów członkowskich z wyjątkiem tych, które przedstawiono w poniższym przykładzie:

1. Konwertowanie konstruktora kopiującego (Zobacz przykład)

1. operator==

1. operator!=

1. allocate

1. alokowany

Domyślny element członkowski języka C++ 11 `construct()` , który zostanie udostępniony dla Ciebie jest idealnym przekazywaniem i umożliwia semantykę przenoszenia, jest znacznie bardziej wydajny w wielu przypadkach niż w przypadku starszej wersji.

> [!WARNING]
> W czasie kompilacji standardowa biblioteka języka C++ używa klasy allocator_traits, aby wykrywać, które elementy członkowskie zostały podane jawnie, i zapewnia implementację domyślną dla wszystkich nieobecnych elementów członkowskich. Nie zakłócaj tego mechanizmu, zapewniając specjalizację allocator_traits dla Twojego alokatora.

W poniższym przykładzie pokazano minimalną implementację alokatora, który używa `malloc` i `free` . Zwróć uwagę na użycie nowego typu wyjątku, `std::bad_array_new_length` który jest zgłaszany, jeśli rozmiar tablicy jest mniejszy niż zero lub większy niż maksymalny dozwolony rozmiar.

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

W języku C++ 03 każdy Alokator używany z kontenerami standardowej biblioteki języka C++ musi implementować następujące definicje typów:

|||
|-|-|
|`const_pointer`|`rebind`|
|`const_reference`|`reference`|
|`difference_type`|`size_type`|
|`pointer`|`value_type`|

Ponadto każdy Alokator używany z kontenerami standardowej biblioteki języka C++ musi implementować następujące metody:

|||
|-|-|
|Konstruktor|`deallocate`|
|Konstruktor kopiujący|`destroy`|
|Destruktor|`max_size`|
|`address`|`operator==`|
|`allocate`|`operator!=`|
|`construct`||

Aby uzyskać więcej informacji na temat tych definicji typów i metod, zobacz [Klasa alokatora](allocator-class.md).

## <a name="see-also"></a>Zobacz też

[Dokumentacja standardowej biblioteki języka C++](cpp-standard-library-reference.md)
