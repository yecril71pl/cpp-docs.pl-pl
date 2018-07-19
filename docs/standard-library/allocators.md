---
title: Allocators — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- allocators
- C++ Standard Library, allocators
ms.assetid: ac95023b-9e7d-49f5-861a-bf7a9a340746
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc84748e35807ef0f270fe8fbbd7560a9a18e3b2
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963498"
---
# <a name="allocators"></a>Allocators

Buforów są używane przez standardowej biblioteki języka C++ do obsługi alokacji i dezalokacji elementy przechowywane w kontenerach. Wszystkie kontenery standardowej biblioteki języka C++ z wyjątkiem std::array mają parametrem szablonu typu `allocator<Type>`, gdzie `Type` reprezentuje typ elementu kontenera. Na przykład klasa vector jest zadeklarowana w następujący sposób:

```cpp
template <
    class Type,
    class Allocator = allocator<Type>
>
class vector
```

Standardowa biblioteka C++ udostępnia domyślną implementację interfejsu dla alokatora. W języku C ++ 11 i nowszych domyślnego alokatora jest aktualizowany do udostępnienia mniejszych interfejs; nosi nazwę nowego programu przydzielania *minimalnych*. W szczególności minimalny alokatora firmy `construct()` element członkowski obsługuje semantykę przenoszenia, co może znacznie poprawić wydajność. W większości przypadków ta domyślnego programu przydzielania powinny być wystarczające. W języku C ++ 11 standardową bibliotekę typów i funkcji podjąć wszystkie alokatora Obsługa parametr typu interfejsu minimalnych, w tym `std::function`, `shared_ptr, allocate_shared()`, i `basic_string`.  Aby uzyskać więcej informacji na temat domyślnego programu przydzielania, zobacz [alokatora klasy](../standard-library/allocator-class.md).

## <a name="writing-your-own-allocator-c11"></a>Zapisywanie swój własny alokator (C ++ 11)

Korzysta z domyślnego programu przydzielania **nowe** i **Usuń** można przydzielić i cofnąć alokacji pamięci. Jeśli chcesz użyć innej metody alokacji pamięci, takich jak przy użyciu pamięci współużytkowanej, należy utworzyć swój własny alokator. Jeśli są przeznaczone dla języka C ++ 11, należy wpisać nowy, niestandardowy alokator ułatwiają alokatora minimalny, jeśli jest to możliwe. Nawet wtedy, gdy zostało już zaimplementowane alokatora w starym stylu, należy wziąć pod uwagę modyfikowania go jako *minimalnych* mogło skorzystać z bardziej wydajne `construct()` metody, która będzie dostępna dla Ciebie automatycznie.

Minimalny alokatora wymaga znacznie mniejszym stopniu deklaratywnie i pozwalają skoncentrować się na `allocate` i `deallocate` funkcji elementów członkowskich, które spełniają wszystkie zadania. Podczas tworzenia alokatora minimalne, nie implementuje żadnych elementów członkowskich, z wyjątkiem tych, jak pokazano w przykładzie poniżej:

1. Konwertowanie konstruktora kopiującego (Zobacz przykład)

1. operator==

1. operator!=

1. allocate

1. Cofnij Przydział

Wartość C ++ 11 domyślna `construct()` elementu członkowskiego, która będzie dostępna dla Ciebie doskonała, przekazywanie i umożliwia przenoszenie semantyki; jest znacznie bardziej efektywne w wielu przypadkach niż starszej wersji.

> [!WARNING]
> W czasie kompilacji standardowej biblioteki C++ klasy allocator_traits wykrywa elementów członkowskich, które podane jawnie i udostępnia domyślną implementację interfejsu dla jakichkolwiek członków, które nie są obecne. Nie zakłóca tego mechanizmu, zapewniając specjalizacja allocator_traits dla Twojego programu przydzielania!

W poniższym przykładzie przedstawiono minimalne wykonanie alokatora, który używa `malloc` i `free`. Zwróć uwagę na użycie nowy typ wyjątku `std::bad_array_new_length` którego jest generowany, jeśli rozmiar tablicy jest mniejsza od zera lub większa niż maksymalny dozwolony rozmiar.

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

## <a name="writing-your-own-allocator-c03"></a>Zapisywanie swój własny alokator (C ++ 03)

W języku C ++ 03 wszelkie alokator używany z kontenerami standardowej biblioteki języka C++, należy zaimplementować następujące definicje typów:

|||
|-|-|
|`const_pointer`|`rebind`|
|`const_reference`|`reference`|
|`difference_type`|`size_type`|
|`pointer`|`value_type`|

Ponadto wszelkie alokator używany z kontenerami standardowej biblioteki języka C++ należy zaimplementować następujące metody:

|||
|-|-|
|Konstruktor|`deallocate`|
|Konstruktor kopiujący|`destroy`|
|Destruktor|`max_size`|
|`address`|`operator==`|
|`allocate`|`operator!=`|
|`construct`||

Aby uzyskać więcej informacji na temat tych definicji typów i metod, zobacz [alokatora klasy](../standard-library/allocator-class.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
