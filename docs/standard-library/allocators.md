---
title: "Allocators — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- allocators
- C++ Standard Library, allocators
ms.assetid: ac95023b-9e7d-49f5-861a-bf7a9a340746
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: eb2c193fd12578e69abef2db555ebbc4fa061e1e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="allocators"></a>Allocators
Allocators — są używane przez standardowa biblioteka C++ do obsługi alokacji i dezalokacji elementy przechowywane w kontenerach. Wszystkie kontenery standardowa biblioteka C++ z wyjątkiem std::array ma parametrem szablonu typu `allocator<Type>`, gdzie `Type` reprezentuje typ kontenera. Na przykład klasa vector jest zadeklarowany w następujący sposób:  
  
```  
template <  
    class Type,  
    class Allocator = allocator<Type>  
>  
class vector  
```  
  
 Standardowa biblioteka C++ udostępnia domyślną implementację dla przydzielania. W języku C ++ 11 i nowszych alokatora domyślne zostało zaktualizowane do uwidacznia interfejsu mniejszych; nowy program przydzielania jest wywoływana *minimalnego alokatora*. W szczególności, minimalnym alokatora przez `construct()` element członkowski obsługuje semantyki przeniesienia, która może znacznie poprawić wydajność. W większości przypadków to alokatora domyślne powinno wystarczyć. W języku C ++ 11 wszystkie biblioteki standardowej typy i funkcje, które zająć alokatora Obsługa parametru typu interfejsu minimalnego alokatora tym `std::function`, `shared_ptr, allocate_shared()`, i `basic_string`.  Aby uzyskać więcej informacji na alokatora domyślne, zobacz [Allocator — klasa](../standard-library/allocator-class.md).  
  
## <a name="writing-your-own-allocator-c11"></a>Pisanie własnych alokatora (C ++ 11)  
 Używa programu przydzielania domyślne `new` i `delete` można przydzielić i cofnięcia przydzielenia pamięci. Jeśli chcesz użyć innej metody przydziału pamięci, na przykład za pomocą pamięci współużytkowanej, należy utworzyć własny przydzielania. Przeznaczona dla języka C ++ 11, należy wpisać nowy, niestandardowy program przydzielania była minimalnego alokatora Jeśli to możliwe. Nawet jeśli już zaimplementowano program przydzielania w starym stylu, zaleca się zmodyfikowanie należy *minimalnego alokatora* Aby korzystać z bardziej wydajne `construct()` metody, które zostaną dostarczone dla Ciebie automatycznie.  
  
 Minimalny alokatora wymaga znacznie mniej typowe i pozwalają skoncentrować się na `allocate` i `deallocate` funkcji elementów członkowskich, które spełniają wszystkie informacje o pracy. Podczas tworzenia alokatora minimalne, nie implementują żadnych elementów członkowskich, z wyjątkiem pól w przykładzie poniżej:  
  
1.  Konwertowanie konstruktora kopiującego (Zobacz przykład)  
  
2.  operator==  
  
3.  operator!=  
  
4.  allocate  
  
5.  Cofnięcie przydziału  
  
 C ++ 11 domyślne `construct()` Członkowskie, które zostaną dostarczone dla Ciebie doskonała, przekazywanie i umożliwia przenoszenie semantyki; jest bardziej wydajne w wielu przypadkach niż starszej wersji.  
  
> [!WARNING]
>  W czasie kompilacji standardowa biblioteka C++ allocator_traits — klasa wykrywa elementów członkowskich, które zostały jawnie podane i udostępnia domyślną implementację dla żadnych elementów członkowskich, które nie są dostępne. Nie zakłóca ten mechanizm, podając specjalizacja allocator_traits — Twoje alokatora!  
  
 W poniższym przykładzie przedstawiono minimalnego wdrożenia programu przydzielania, która używa `malloc` i `free`. Zwróć uwagę na użycie nowego typu wyjątku `std::bad_array_new_length` który jest generowany, jeśli rozmiar tablicy jest mniejsza niż zero lub większa niż maksymalny dozwolony rozmiar.  
  
```  
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
  
## <a name="writing-your-own-allocator-c03"></a>Pisanie własnych alokatora (03 C ++)  
 W języku C ++ 03 wszelkie alokatora używane z kontenerami standardowa biblioteka C++ musi implementować następujące definicje typów:  
  
|||  
|-|-|  
|`const_pointer`|`rebind`|  
|`const_reference`|`reference`|  
|`difference_type`|`size_type`|  
|`pointer`|`value_type`|  
  
 Ponadto wszystkie alokatora używane z kontenerami standardowa biblioteka C++ musi implementować następujące metody:  
  
|||  
|-|-|  
|Konstruktor|`deallocate`|  
|Konstruktor kopiujący|`destroy`|  
|Destruktor|`max_size`|  
|`address`|`operator==`|  
|`allocate`|`operator!=`|  
|`construct`||  
  
 Aby uzyskać więcej informacji o tych definicje typów i metod, zobacz [Allocator — klasa](../standard-library/allocator-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)




