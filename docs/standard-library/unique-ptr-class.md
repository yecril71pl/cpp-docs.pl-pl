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
ms.openlocfilehash: 694ea94ac0e9dcd31d89a3a83bd3400bac3e8e4f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222189"
---
# <a name="unique_ptr-class"></a>unique_ptr — Klasa

Przechowuje wskaźnik do posiadanego obiektu lub tablicy. Obiekt/tablica nie jest własnością żadnego innego `unique_ptr` . Obiekt/tablica jest niszczona, gdy `unique_ptr` zostanie zniszczona.

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

*Kliknij*\
Klasa `unique_ptr`.

*Nptr*\
`rvalue`Typu `std::nullptr_t` .

*PTR*\
Klasa `pointer`.

*Deleter*\
`deleter`Funkcja, która jest powiązana z `unique_ptr` .

## <a name="exceptions"></a>Wyjątki

Żadne wyjątki nie są generowane przez program `unique_ptr` .

## <a name="remarks"></a>Uwagi

`unique_ptr`Klasa zastępuje `auto_ptr` i może być używana jako element kontenerów standardowej biblioteki języka C++.

Użyj funkcji pomocnika [make_unique](../standard-library/memory-functions.md#make_unique) , aby efektywnie utworzyć nowe wystąpienia programu `unique_ptr` .

`unique_ptr`unikatowy sposób zarządzania zasobem. Każdy `unique_ptr` obiekt przechowuje wskaźnik do obiektu, do którego należy, lub przechowuje wskaźnik o wartości null. Zasób może być własnością nie więcej niż jednego `unique_ptr` obiektu;  gdy `unique_ptr` obiekt będący właścicielem określonego zasobu jest niszczony, zasób zostanie zwolniony. `unique_ptr`Obiekt może zostać przeniesiony, ale nie skopiowany;  Aby uzyskać więcej informacji, zobacz [rvalue Reference deklarator:  &&](../cpp/rvalue-reference-declarator-amp-amp.md).

Zasób jest bezpłatny przez wywołanie przechowywanego `deleter` obiektu typu `Del` , który wie, jak zasoby są przydzielone do określonego `unique_ptr` . Domyślnie zakłada się, `deleter` `default_delete<T>` że zasób wskazywany przez `ptr` jest przydzielony z **`new`** i że może być zwolniony przez wywołanie `delete _Ptr` . (Częściowa specjalizacja `unique_ptr<T[]>` zarządza obiektami tablic przydzielonymi z `new[]` i ma domyślne `deleter` `default_delete<T[]>` , wyspecjalizowane dla wywołania delete [] `ptr` ).

Przechowywany wskaźnik do należącego do niego zasobu `stored_ptr` ma typ `pointer` . Jest on `Del::pointer` zdefiniowany, a `T *` Jeśli nie. Przechowywany `deleter` obiekt `stored_deleter` zajmuje brak spacji w obiekcie, jeśli `deleter` nie jest bezstanowy. Zwróć uwagę, że `Del` może to być typ referencyjny.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[unique_ptr](#unique_ptr)|Istnieje siedem konstruktorów dla programu `unique_ptr` .|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[deleter_type](#deleter_type)|Synonim dla parametru szablonu `Del` .|
|[element_type](#element_type)|Synonim dla parametru szablonu `T` .|
|[pointer](#pointer)|Synonim dla `Del::pointer` if zdefiniowane, w przeciwnym razie `T *` .|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[Pobierz](#get)|Zwraca wartość `stored_ptr`.|
|[get_deleter](#get_deleter)|Zwraca odwołanie do `stored_deleter` .|
|[Usuwanie](#release)|przechowuje `pointer()` w `stored_ptr` i zwraca poprzednią zawartość.|
|[zresetować](#reset)|Zwalnia aktualnie posiadany zasób i akceptuje nowy zasób.|
|[wymiany](#swap)|Wymienia zasób i `deleter` z podanym `unique_ptr` .|

### <a name="operators"></a>Operatory

|||
|-|-|
|**wartość logiczna operatora**|Operator zwraca wartość typu, który jest konwertowany na **`bool`** . Wynikiem konwersji **`bool`** jest **`true`** `get() != pointer()` , gdy, w przeciwnym razie **`false`** .|
|`operator->`|Funkcja członkowska zwraca wartość `stored_ptr` .|
|`operator*`|Funkcja członkowska zwraca wartość `*stored_ptr` .|
|[operator =](#unique_ptr_operator_eq)|Przypisuje wartość `unique_ptr` (lub `pointer-type` ) do bieżącej `unique_ptr` .|

### <a name="deleter_type"></a><a name="deleter_type"></a>deleter_type

Typ jest synonimem dla parametru szablonu `Del` .

```cpp
typedef Del deleter_type;
```

#### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Del` .

### <a name="element_type"></a><a name="element_type"></a>element_type

Typ jest synonimem dla parametru szablonu `Type` .

```cpp
typedef Type element_type;
```

#### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Ty` .

### <a name="get"></a><a name="get"></a>Pobierz

Zwraca wartość `stored_ptr`.

```cpp
pointer get() const;
```

#### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca wartość `stored_ptr` .

### <a name="get_deleter"></a><a name="get_deleter"></a>get_deleter

Zwraca odwołanie do `stored_deleter` .

```cpp
Del& get_deleter();

const Del& get_deleter() const;
```

#### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca odwołanie do `stored_deleter` .

### <a name="operator"></a><a name="unique_ptr_operator_eq"></a>operator =

Przypisuje adres dostarczonego elementu `unique_ptr` do bieżącego obiektu.

```cpp
unique_ptr& operator=(unique_ptr&& right);
template <class U, Class Del2>
unique_ptr& operator=(unique_ptr<Type, Del>&& right);
unique_ptr& operator=(pointer-type);
```

#### <a name="parameters"></a>Parametry

`unique_ptr`Odwołanie używane do przypisywania wartości do bieżącego elementu `unique_ptr` .

#### <a name="remarks"></a>Uwagi

Funkcja członkowska wywołuje `reset(right.release())` i przenosi `right.stored_deleter` do `stored_deleter` , a następnie zwraca **`*this`** .

### <a name="pointer"></a><a name="pointer"></a>przytrzymaj

Synonim dla `Del::pointer` if zdefiniowane, w przeciwnym razie `Type *` .

```cpp
typedef T1 pointer;
```

#### <a name="remarks"></a>Uwagi

Typ jest synonimem `Del::pointer` , jeśli jest zdefiniowany, w przeciwnym razie `Type *` .

### <a name="release"></a><a name="release"></a>Usuwanie

Zwalnia własność zwróconego, przechowywanego wskaźnika do obiektu wywołującego i ustawia wartość przechowywanego wskaźnika na **`nullptr`** .

```cpp
pointer release();
```

#### <a name="remarks"></a>Uwagi

Służy `release` do przejęcia własności surowego wskaźnika przechowywanego przez `unique_ptr` . Obiekt wywołujący jest odpowiedzialny za usunięcie zwróconego wskaźnika. `unique-ptr`Jest ustawiony na pusty, skonstruowany stan domyślny. Można przypisać inny wskaźnik typu zgodnego do elementu `unique_ptr` po wywołaniu `release` .

#### <a name="example"></a>Przykład

W tym przykładzie pokazano, jak obiekt wywołujący wydania jest odpowiedzialny za zwracanego obiektu:

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

### <a name="reset"></a><a name="reset"></a>zresetować

Przejmuje własność parametru wskaźnika, a następnie usuwa oryginalny, przechowywany wskaźnik. Jeśli nowy wskaźnik jest taki sam jak oryginalny, przechowywany wskaźnik, `reset` usuwa wskaźnik i ustawia wartość przechowywanego wskaźnika **`nullptr`** .

```cpp
void reset(pointer ptr = pointer());
void reset(nullptr_t ptr);
```

#### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik do zasobu do przejęcia na własność.

#### <a name="remarks"></a>Uwagi

Służy `reset` do zmiany przechowywanego [wskaźnika](#pointer) należącego `unique_ptr` do, *ptr* a następnie usuwania oryginalnego, przechowywanego wskaźnika. Jeśli wartość `unique_ptr` nie jest pusta, `reset` wywołuje funkcję delete zwracaną przez [get_deleter](#get_deleter) na oryginalnym przechowywanym wskaźniku.

Ponieważ `reset` program najpierw zapisuje nowy wskaźnik *PTR*, a następnie usuwa oryginalny, przechowywany wskaźnik, można `reset` natychmiast usunąć *PTR* , jeśli jest taki sam, jak oryginalny, przechowywany wskaźnik.

### <a name="swap"></a><a name="swap"></a>wymiany

Wymienia wskaźniki między dwoma `unique_ptr` obiektami.

```cpp
void swap(unique_ptr& right);
```

#### <a name="parameters"></a>Parametry

*Kliknij*\
`unique_ptr`Używany do zamiany wskaźników.

#### <a name="remarks"></a>Uwagi

Funkcja członkowska jest zamieniana `stored_ptr` z `right.stored_ptr` i `stored_deleter` z `right.stored_deleter` .

### <a name="unique_ptr"></a><a name="unique_ptr"></a>unique_ptr

Istnieje siedem konstruktorów dla programu `unique_ptr` .

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
Wskaźnik do zasobu, który ma zostać przypisany do `unique_ptr` .

*_Deleter*\
A, `deleter` który ma zostać przypisany do `unique_ptr` .

*Kliknij*\
`rvalue reference`Do, `unique_ptr` z którego `unique_ptr` pola są przesuwane do nowo skonstruowanych `unique_ptr` .

#### <a name="remarks"></a>Uwagi

Pierwsze dwa konstruktory konstruują obiekt, który zarządza brakiem zasobów. Trzeci Konstruktor przechowuje *PTR* w `stored_ptr` . Czwarty Konstruktor przechowuje *PTR* w `stored_ptr` i `deleter` w `stored_deleter` .

Piąty Konstruktor przechowuje *PTR* w `stored_ptr` i przenosi `deleter` do `stored_deleter` . Szóste i siódme konstruktory przechowują `right.release()` `stored_ptr` i przenosiją się `right.get_deleter()` do `stored_deleter` .

### <a name="unique_ptr"></a><a name="dtorunique_ptr"></a>~ unique_ptr

Destruktor dla `unique_ptr` , niszczy `unique_ptr` obiekt.

```cpp
~unique_ptr();
```

#### <a name="remarks"></a>Uwagi

Destruktor wywołuje `get_deleter()(stored_ptr)` .
