---
title: unique_ptr — Klasa
ms.date: 11/04/2016
f1_keywords:
- memory/std::unique_ptr
- memory/std::unique_ptr::deleter_type
- memory/std::unique_ptr::element_type
- memory/std::unique_ptr::pointer
- memory/std::unique_ptr::get
- memory/std::unique_ptr::get_deleter
- memory/std::unique_ptr::release
- memory/std::unique_ptr::reset
- memory/std::unique_ptr::swap
helpviewer_keywords:
- std::unique_ptr [C++]
- std::unique_ptr [C++], deleter_type
- std::unique_ptr [C++], element_type
- std::unique_ptr [C++], pointer
- std::unique_ptr [C++], get
- std::unique_ptr [C++], get_deleter
- std::unique_ptr [C++], release
- std::unique_ptr [C++], reset
- std::unique_ptr [C++], swap
ms.assetid: acdf046b-831e-4a4a-83aa-6d4ee467db9a
ms.openlocfilehash: 3aff30e2e23feb85c6b93d79ddd4552849d3ba05
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243471"
---
# <a name="uniqueptr-class"></a>unique_ptr — Klasa

Przechowuje wskaźnik do posiadanego obiektu lub tablicy. Obiekt/tablicy jest własnością żadnego innego `unique_ptr`. Obiekt/tablicy jest niszczony, gdy `unique_ptr` zostanie zniszczony.

## <a name="syntax"></a>Składnia

```cpp
class unique_ptr {
public:
    unique_ptr();
    unique_ptr(nullptr_t Nptr);
    explicit unique_ptr(pointer Ptr);
    unique_ptr(pointer Ptr,
        typename conditional<is_reference<Del>::value, Del,
        typename add_reference<const Del>::type>::type Deleter);
    unique_ptr(pointer Ptr,
        typename remove_reference<Del>::type&& Deleter);
    unique_ptr(unique_ptr&& Right);
    template <class T2, Class Del2>
    unique_ptr(unique_ptr<T2, Del2>&& Right);
    unique_ptr(const unique_ptr& Right) = delete;
    unique_ptr& operator=(const unique_ptr& Right) = delete;
};

//Specialization for arrays:
template <class T, class D>
class unique_ptr<T[], D> {
public:
    typedef pointer;
    typedef T element_type;
    typedef D deleter_type;
    constexpr unique_ptr() noexcept;
    template <class U>
    explicit unique_ptr(U p) noexcept;
    template <class U>
    unique_ptr(U p, see below d) noexcept;
    template <class U>
    unique_ptr(U p, see below d) noexcept;
    unique_ptr(unique_ptr&& u) noexcept;
    constexpr unique_ptr(nullptr_t) noexcept : unique_ptr() { }     template <class U, class E>
        unique_ptr(unique_ptr<U, E>&& u) noexcept;
    ~unique_ptr();
    unique_ptr& operator=(unique_ptr&& u) noexcept;
    template <class U, class E>
    unique_ptr& operator=(unique_ptr<U, E>&& u) noexcept;
    unique_ptr& operator=(nullptr_t) noexcept;
    T& operator[](size_t i) const;

    pointer get() const noexcept;
    deleter_type& get_deleter() noexcept;
    const deleter_type& get_deleter() const noexcept;
    explicit operator bool() const noexcept;
    pointer release() noexcept;
    void reset(pointer p = pointer()) noexcept;
    void reset(nullptr_t = nullptr) noexcept;
    template <class U>
    void reset(U p) noexcept = delete;
    void swap(unique_ptr& u) noexcept;  // disable copy from lvalue unique_ptr(const unique_ptr&) = delete;
    unique_ptr& operator=(const unique_ptr&) = delete;
};
```

### <a name="parameters"></a>Parametry

*po prawej stronie*\
A `unique_ptr`.

*Nptr*\
`rvalue` Typu `std::nullptr_t`.

*PTR*\
A `pointer`.

*Deleter*\
A `deleter` funkcja, która jest powiązana z `unique_ptr`.

## <a name="exceptions"></a>Wyjątki

Żadne wyjątki generowane przez `unique_ptr`.

## <a name="remarks"></a>Uwagi

`unique_ptr` Zastępuje klasy `auto_ptr`i może służyć jako element kontenerów standardowej biblioteki języka C++.

Użyj [make_unique](../standard-library/memory-functions.md#make_unique) funkcja pomocnika służąca do wydajnego tworzenia nowych wystąpień `unique_ptr`.

`unique_ptr` jednoznacznie zarządza zasobem. Każdy `unique_ptr` obiekt przechowuje wskaźnik do obiektu, który posiada lub przechowuje wskaźnik zerowy. Zasób może być własnością tylko jednego `unique_ptr` obiektu;  gdy `unique_ptr` niszczony jest obiekt, który posiada określony zasób, zasób zostanie zwolniony. Element `unique_ptr` obiektu może być przeniesiony, ale nie można go kopiować;  Aby uzyskać więcej informacji, zobacz [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

Zasób zostanie zwolniony przez wywołanie przechowywanego `deleter` obiektu typu `Del` który wie, jak zasoby są przydzielane dla danego `unique_ptr`. Wartość domyślna `deleter` `default_delete<T>` przyjęto założenie, że zasób wskazywany przez `ptr` została przydzielona z `new`, i który może zostać uwolniony przez wywołanie metody `delete _Ptr`. (Częściowa specjalizacja `unique_ptr<T[]>`zarządza obiektami tablicy przydzielonymi `new[]`, i ma domyślny `deleter` `default_delete<T[]>`, wyspecjalizowany w celu wywoływania delete [] `ptr`.)

Przechowywany wskaźnik do zasobu będącego własnością `stored_ptr` ma typ `pointer`. Jest `Del::pointer` Jeśli zdefiniowane, a `T *` w przeciwnym razie. Przechowywany `deleter` obiektu `stored_deleter` nie zajmuje miejsca w obiekcie Jeśli `deleter` jest bezstanowy. Należy pamiętać, że `Del` może być typem referencyjnym.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|||
|-|-|
|[unique_ptr](#unique_ptr)|Istnieje siedem konstruktorów `unique_ptr`.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[deleter_type](#deleter_type)|Synonim dla parametru szablonu `Del`.|
|[element_type](#element_type)|Synonim dla parametru szablonu `T`.|
|[pointer](#pointer)|Synonim dla `Del::pointer` Jeśli zdefiniowane, w przeciwnym razie `T *`.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[get](#get)|Zwraca `stored_ptr`.|
|[get_deleter](#get_deleter)|Zwraca odwołanie do `stored_deleter`.|
|[Wydania](#release)|przechowuje `pointer()` w `stored_ptr` i zwraca jego poprzednią zawartość.|
|[Resetuj](#reset)|Zwalnia aktualnie posiadany zasób i akceptuje nowy zasób.|
|[swap](#swap)|Wymienia zasób i `deleter` z dostępnego `unique_ptr`.|

### <a name="operators"></a>Operatory

|||
|-|-|
|**bool — operator**|Operator zwraca wartość typu, który jest konwertowany na **bool**. Wynik konwersji **bool** jest **true** podczas `get() != pointer()`, w przeciwnym razie **false**.|
|`operator->`|Funkcja elementu członkowskiego zwraca `stored_ptr`.|
|`operator*`|Funkcja elementu członkowskiego zwraca `*stored_ptr`.|
|[operator=](#unique_ptr_operator_eq)|Przypisuje wartość `unique_ptr` (lub `pointer-type`) do bieżącego `unique_ptr`.|

### <a name="deleter_type"></a> deleter_type

Typ jest synonimem dla parametru szablonu `Del`.

```cpp
typedef Del deleter_type;
```

#### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Del`.

### <a name="element_type"></a> ELEMENT_TYPE

Typ jest synonimem dla parametru szablonu `Type`.

```cpp
typedef Type element_type;
```

#### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Ty`.

### <a name="get"></a> Pobierz

Zwraca `stored_ptr`.

```cpp
pointer get() const;
```

#### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `stored_ptr`.

### <a name="get_deleter"></a> get_deleter —

Zwraca odwołanie do `stored_deleter`.

```cpp
Del& get_deleter();

const Del& get_deleter() const;
```

#### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwołanie do `stored_deleter`.

### <a name="unique_ptr_operator_eq"></a> operator =

Przypisuje adres podany `unique_ptr` do bieżącej.

```cpp
unique_ptr& operator=(unique_ptr&& right);
template <class U, Class Del2>
unique_ptr& operator=(unique_ptr<Type, Del>&& right);
unique_ptr& operator=(pointer-type);
```

#### <a name="parameters"></a>Parametry

A `unique_ptr` odwołania używane do przypisywania wartości do bieżącego `unique_ptr`.

#### <a name="remarks"></a>Uwagi

Element członkowski funkcji wywołanie `reset(right.release())` i Przenieś `right.stored_deleter` do `stored_deleter`, a następnie wróć `*this`.

### <a name="pointer"></a> Wskaźnik

Synonim dla `Del::pointer` Jeśli zdefiniowane, w przeciwnym razie `Type *`.

```cpp
typedef T1 pointer;
```

#### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `Del::pointer` Jeśli zdefiniowane, w przeciwnym razie `Type *`.

### <a name="release"></a> Wydania

Zwalnia własność zwrócone przechowywany wskaźnik do obiektu wywołującego i ustawia wartość przechowywany wskaźnik **nullptr**.

```cpp
pointer release();
```

#### <a name="remarks"></a>Uwagi

Użyj `release` przejąć własność surowy wskaźnik przechowywane przez `unique_ptr`. Obiekt wywołujący jest odpowiedzialny za usunięcie zwrócony wskaźnik. `unique-ptr` Ustawiono stan zbudowanego domyślnie puste. Możesz przypisać inny wskaźnik zgodne z typem `unique_ptr` po wywołaniu `release`.

#### <a name="example"></a>Przykład

Ten przykład pokazuje, jak jest odpowiedzialny za zwrócony obiekt wywołujący wersji:

```cpp
// stl_release_unique.cpp
// Compile by using: cl /W4 /EHsc stl_release_unique.cpp
#include <iostream>
#include <memory>

struct Sample {
   int content_;
   Sample(int content) : content_(content) {
      std::cout << "Constructing Sample(" << content_ << ")" << std::endl;
   }
   ~Sample() {
      std::cout << "Deleting Sample(" << content_ << ")" << std::endl;
   }
};

void ReleaseUniquePointer() {
   // Use make_unique function when possible.
   auto up1 = std::make_unique<Sample>(3);
   auto up2 = std::make_unique<Sample>(42);

   // Take over ownership from the unique_ptr up2 by using release
   auto ptr = up2.release();
   if (up2) {
      // This statement does not execute, because up2 is empty.
      std::cout << "up2 is not empty." << std::endl;
   }
   // We are now responsible for deletion of ptr.
   delete ptr;
   // up1 deletes its stored pointer when it goes out of scope.
}

int main() {
   ReleaseUniquePointer();
}
```

```Output
Constructing Sample(3)
Constructing Sample(42)
Deleting Sample(42)
Deleting Sample(3)
```

### <a name="reset"></a> Resetuj

Przejmuje na własność parametru wskaźnika, a następnie usuwa oryginalny przechowywany wskaźnik. Jeśli nowy wskaźnik jest taki sam jak oryginalne przechowywany wskaźnik `reset` usuwa wskaźnika i ustawia przechowywany wskaźnik **nullptr**.

```cpp
void reset(pointer ptr = pointer());
void reset(nullptr_t ptr);
```

#### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik do zasobu, aby przejąć prawo własności.

#### <a name="remarks"></a>Uwagi

Użyj `reset` zmienić przechowywaną [wskaźnik](#pointer) własnością `unique_ptr` do *ptr* , a następnie usuń oryginalny przechowywany wskaźnik. Jeśli `unique_ptr` nie jest pusta, `reset` wywołuje funkcję deleter zwrócone przez [get_deleter —](#get_deleter) na oryginalnym przechowywany wskaźnik.

Ponieważ `reset` najpierw przechowuje nowy wskaźnik *ptr*, a następnie usuwa oryginalny przechowywany wskaźnik, możliwe jest `reset` można natychmiast usunąć *ptr* Jeśli jest taka sama jak oryginalny przechowywany wskaźnik.

### <a name="swap"></a> swap

Wymienia wskaźników między dwoma `unique_ptr` obiektów.

```cpp
void swap(unique_ptr& right);
```

#### <a name="parameters"></a>Parametry

*po prawej stronie*\
A `unique_ptr` umożliwiają zamienianie wskaźników.

#### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zamienia `stored_ptr` z `right.stored_ptr` i `stored_deleter` z `right.stored_deleter`.

### <a name="unique_ptr"></a> unique_ptr

Istnieje siedem konstruktorów `unique_ptr`.

```cpp
unique_ptr();

unique_ptr(nullptr_t);
explicit unique_ptr(pointer ptr);

unique_ptr(
    Type* ptr,
    typename conditional<
    is_reference<Del>::value,
    Del,
    typename add_reference<const Del>::type>::type _Deleter);

unique_ptr(pointer ptr, typename remove_reference<Del>::type&& _Deleter);
unique_ptr(unique_ptr&& right);
template <class Ty2, Class Del2>
    unique_ptr(unique_ptr<Ty2, Del2>&& right);
```

#### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik do zasobu, który ma być przypisane do `unique_ptr`.

*_Deleter*\
A `deleter` ma być przypisane do `unique_ptr`.

*po prawej stronie*\
`rvalue reference` Do `unique_ptr` z którego `unique_ptr` pola są przypisane do nowo skonstruowany przenoszenia `unique_ptr`.

#### <a name="remarks"></a>Uwagi

Dwa pierwsze konstruktory skonstruować obiekt, który zarządza żaden z zasobów. Trzeci Konstruktor magazynów *ptr* w `stored_ptr`. Czwarty Konstruktor magazynów *ptr* w `stored_ptr` i `deleter` w `stored_deleter`.

Piąty Konstruktor magazynów *ptr* w `stored_ptr` i przenosi `deleter` do `stored_deleter`. Magazyn konstruktory szóstego i siódmego `right.release()` w `stored_ptr` i przenosi `right.get_deleter()` do `stored_deleter`.

### <a name="dtorunique_ptr"></a> ~ unique_ptr

Destruktor dla `unique_ptr`, niszczy `unique_ptr` obiektu.

```cpp
~unique_ptr();
```

#### <a name="remarks"></a>Uwagi

Wywołania destruktora `get_deleter()(stored_ptr)`.
