---
title: reference_wrapper — Klasa
ms.date: 11/04/2016
f1_keywords:
- functional/std::reference_wrapper
- type_traits/std::reference_wrapper
- xrefwrap/std::reference_wrapper
- type_traits/std::reference_wrapper::get
- type_traits/std::reference_wrapper::operator()
- functional/std::reference_wrapper::result_type
- functional/std::reference_wrapper::type
- functional/std::reference_wrapper::get
- functional/std::reference_wrapper::operator()
helpviewer_keywords:
- std::reference_wrapper [C++]
- std::reference_wrapper [C++]
- std::reference_wrapper [C++], result_type
- std::reference_wrapper [C++], type
- std::reference_wrapper [C++], get
ms.assetid: 90b8ed62-e6f1-44ed-acc7-9619bd58865a
ms.openlocfilehash: 623e1480bdec85120e504c8dc71b28d017c8872a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845071"
---
# <a name="reference_wrapper-class"></a>reference_wrapper — Klasa

Zawija odwołanie.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
class reference_wrapper
{
    typedef Ty type;

    reference_wrapper(Ty&) noexcept;
    operator Ty&() const noexcept;
    Ty& get() const noexcept;

    template <class... Types>
    auto operator()(Types&&... args) const ->
        decltype(std::invoke(get(), std::forward<Types>(args)...));
};
```

## <a name="remarks"></a>Uwagi

A `reference_wrapper<Ty>` to konstrukcyjną kopiowania i kopiowania otoki, którą można przypisać do obiektu lub funkcji typu `Ty` , i zawiera wskaźnik wskazujący obiekt tego typu. `reference_wrapper`Może służyć do przechowywania odwołań w standardowych kontenerach oraz do przekazywania obiektów przez odwołanie do `std::bind` .

Typ `Ty` musi być typem obiektu lub typem funkcji albo potwierdzenie statyczne kończy się w czasie kompilacji.

Funkcje pomocnicze [std:: ref](functional-functions.md#ref) i [std:: cref](functional-functions.md#cref) mogą służyć do tworzenia `reference_wrapper` obiektów.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktory

|Nazwa|Opis|
|-|-|
|[reference_wrapper](#reference_wrapper)|Konstruuje a `reference_wrapper` .|

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|-|-|
|[result_type](#result_type)|Słaby typ wyniku opakowanego odwołania.|
|[Wprowadź](#type)|Typ odwołania opakowanego.|

### <a name="functions"></a>Functions

|Nazwa|Opis|
|-|-|
|[Pobierz](#get)|Uzyskuje opakowane odwołanie.|

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|-|-|
|[operator ty&amp;](#op_ty_amp)|Pobiera wskaźnik do opakowanego odwołania.|
|[operator ()](#op_call)|Wywołuje opakowane odwołanie.|

## <a name="get"></a><a name="get"></a> Pobierz

Uzyskuje opakowane odwołanie.

```cpp
Ty& get() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca opakowane odwołanie.

### <a name="example"></a>Przykład

```cpp
// std__functional__reference_wrapper_get.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int main() {
    int i = 1;
    std::reference_wrapper<int> rwi(i);

    std::cout << "i = " << i << std::endl;
    std::cout << "rwi = " << rwi << std::endl;
    rwi.get() = -1;
    std::cout << "i = " << i << std::endl;

    return (0);
}
```

```Output
i = 1
rwi = 1
i = -1
```

## <a name="operator-tyamp"></a><a name="op_ty_amp"></a> operator ty&amp;

Pobiera opakowane odwołanie.

```cpp
operator Ty&() const noexcept;
```

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca `*ptr` .

### <a name="example"></a>Przykład

```cpp
// std__functional__reference_wrapper_operator_cast.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int main() {
    int i = 1;
    std::reference_wrapper<int> rwi(i);

    std::cout << "i = " << i << std::endl;
    std::cout << "(int)rwi = " << (int)rwi << std::endl;

    return (0);
}
```

```Output
i = 1
(int)rwi = 1
```

## <a name="operator"></a><a name="op_call"></a> operator ()

Wywołuje opakowane odwołanie.

```cpp
template <class... Types>
auto operator()(Types&&... args);
```

### <a name="parameters"></a>Parametry

*Typ*\
Typy listy argumentów.

*argumentów*\
Lista argumentów.

### <a name="remarks"></a>Uwagi

Element członkowski szablonu `operator()` zwraca wartość `std::invoke(get(), std::forward<Types>(args)...)` .

### <a name="example"></a>Przykład

```cpp
// std__functional__reference_wrapper_operator_call.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    std::reference_wrapper<int (int)> rwi(neg);

    std::cout << "rwi(3) = " << rwi(3) << std::endl;

    return (0);
}
```

```Output
rwi(3) = -3
```

## <a name="reference_wrapper"></a><a name="reference_wrapper"></a> reference_wrapper

Konstruuje a `reference_wrapper` .

```cpp
reference_wrapper(Ty& val) noexcept;
```

### <a name="parameters"></a>Parametry

*Br*\
Typ do oblewania.

*użyte*\
Wartość do zawinięcia.

### <a name="remarks"></a>Uwagi

Konstruktor ustawia wartość przechowywaną `ptr` na `&val` .

### <a name="example"></a>Przykład

```cpp
// std__functional__reference_wrapper_reference_wrapper.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    int i = 1;
    std::reference_wrapper<int> rwi(i);

    std::cout << "i = " << i << std::endl;
    std::cout << "rwi = " << rwi << std::endl;
    rwi.get() = -1;
    std::cout << "i = " << i << std::endl;

    return (0);
}
```

```Output
i = 1
rwi = 1
i = -1
```

## <a name="result_type"></a><a name="result_type"></a> result_type

Słaby typ wyniku opakowanego odwołania.

```cpp
typedef R result_type;
```

### <a name="remarks"></a>Uwagi

`result_type`Element typedef jest synonimem dla słabego typu wyniku funkcji opakowanej. Ten element typedef jest istotny tylko dla typów funkcji.

### <a name="example"></a>Przykład

```cpp
// std__functional__reference_wrapper_result_type.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    typedef std::reference_wrapper<int (int)> Mywrapper;
    Mywrapper rwi(neg);
    Mywrapper::result_type val = rwi(3);

    std::cout << "val = " << val << std::endl;

    return (0);
}
```

```Output
val = -3
```

## <a name="type"></a><a name="type"></a> Wprowadź

Typ odwołania opakowanego.

```cpp
typedef Ty type;
```

### <a name="remarks"></a>Uwagi

Element typedef jest synonimem argumentu szablonu `Ty` .

### <a name="example"></a>Przykład

```cpp
// std__functional__reference_wrapper_type.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    int i = 1;
    typedef std::reference_wrapper<int> Mywrapper;
    Mywrapper rwi(i);
    Mywrapper::type val = rwi.get();

    std::cout << "i = " << i << std::endl;
    std::cout << "rwi = " << val << std::endl;

    return (0);
}
```

```Output
i = 1
rwi = 1
```
