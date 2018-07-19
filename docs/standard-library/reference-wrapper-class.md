---
title: reference_wrapper — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- std::reference_wrapper [C++]
- std::reference_wrapper [C++]
- std::reference_wrapper [C++], result_type
- std::reference_wrapper [C++], type
- std::reference_wrapper [C++], get
ms.assetid: 90b8ed62-e6f1-44ed-acc7-9619bd58865a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70ffecdfdf661e7423a4db0898b05dfa2f5ce832
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954646"
---
# <a name="referencewrapper-class"></a>reference_wrapper — Klasa

Opakowuje odwołania.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
class reference_wrapper
{
public:
    typedef Ty type;

    reference_wrapper(Ty&) noexcept;
    operator Ty&() const noexcept;
    Ty& get() const noexcept;

    template <class... Types>
    auto operator()(Types&&... args) const ->
        decltype(std::invoke(get(), std::forward<Types>(args)...));

private:
    Ty *ptr; // exposition only
};
```

## <a name="remarks"></a>Uwagi

A `reference_wrapper<Ty>` kopiowania konstrukcyjną i kopiowania można przypisać otokę odwołanie do obiektu lub funkcji typu `Ty`i przechowuje wskaźnika, który wskazuje na obiekt tego typu. A `reference_wrapper` może służyć do przechowywania odwołań w standardowych kontenerów, a także do przekazywania obiektów w odniesieniu do `std::bind`.

Typ `Ty` musi być typu obiektu lub typu funkcji lub asercja statyczna kończy się niepowodzeniem w czasie kompilacji.

Funkcje pomocnicze [std::ref](functional-functions.md#ref) i [std::cref](functional-functions.md#cref) może służyć do tworzenia `reference_wrapper` obiektów.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[reference_wrapper —](#reference_wrapper)|Konstruuje `reference_wrapper`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[result_type](#result_type)|Typ wyniku słabe odwołanie opakowana.|
|[Typ](#type)|Typ opakowany odwołania.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[get](#get)|Pobiera opakowany odwołania.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[reference_wrapper::operator Ty&amp;](#op_ty_amp)|Pobiera wskaźnik do odwołania opakowana.|
|[reference_wrapper::operator()](#op_call)|Wywołuje opakowana odwołania.|
## <a name="requirements"></a>Wymagania

**Nagłówek:** \<funkcjonalności >

**Namespace:** standardowe

## <a name="get"></a>  reference_wrapper::Get

Pobiera opakowany odwołania.

```cpp
Ty& get() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca odwołanie opakowana.

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

## <a name="op_ty_amp"></a>  reference_wrapper::operator Ty&amp;

Pobiera odniesienie opakowana.

```cpp
operator Ty&() const noexcept;
```

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca `*ptr`.

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

## <a name="op_call"></a>  reference_wrapper::operator()

Wywołuje opakowana odwołania.

```cpp
template <class... Types>
auto operator()(Types&&... args);
```

### <a name="parameters"></a>Parametry

*Typy* typy listy argumentów.

*argumenty* listy argumentów.

### <a name="remarks"></a>Uwagi

Szablon elementu członkowskiego `operator()` zwraca `std::invoke(get(), std::forward<Types>(args)...)`.

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

## <a name="reference_wrapper"></a>  reference_wrapper::reference_wrapper

Konstruuje `reference_wrapper`.

```cpp
reference_wrapper(Ty& val) noexcept;
```

### <a name="parameters"></a>Parametry

*Ty* typu do opakowania.

*Val* wartość do zakodowania.

### <a name="remarks"></a>Uwagi

Konstruktor określa wartości przechowywanej `ptr` do `&val`.

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

## <a name="result_type"></a>  reference_wrapper::result_type

Typ wyniku słabe odwołanie opakowana.

```cpp
typedef R result_type;
```

### <a name="remarks"></a>Uwagi

`result_type` Typedef jest synonimem dla typ wyniku słabe opakowana funkcja. Ten element typedef jest przydatny tylko dla typów funkcji.

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

## <a name="type"></a>  reference_wrapper::type

Typ opakowany odwołania.

```cpp
typedef Ty type;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem dla argumentu szablonu `Ty`.

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

## <a name="see-also"></a>Zobacz także

[cref](../standard-library/functional-functions.md#cref)<br/>
[ref](../standard-library/functional-functions.md#ref)<br/>
