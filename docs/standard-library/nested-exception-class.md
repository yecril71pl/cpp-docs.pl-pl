---
title: Klasa nested_exception
ms.date: 11/04/2016
f1_keywords:
- exception/std::bad_exception
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: 5741b3aa255f915500f5fe79ab5374c8c86f8814
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460178"
---
# <a name="nestedexception-class"></a>Klasa nested_exception

Klasa opisuje wyjątek do użycia z wielokrotnym dziedziczeniem. Przechwytuje aktualnie obsłużony wyjątek i zapisuje go do późniejszego użycia.

## <a name="syntax"></a>Składnia

```cpp
class nested_exception {
    public:
        nested_exception();
        nested_exception(const nested_exception&) = default;
        virtual ~nested_exception() = default; // access functions
};
```

## <a name="members"></a>Elementy członkowskie

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator=](#op_as)||

### <a name="functions"></a>Funkcje

|||
|-|-|
|[rethrow_nested](#rethrow_nested)|Zgłasza wyjątek przechowywany.|
|[nested_ptr](#nested_ptr)|Zwraca przechowywany wyjątek.|

### <a name="op_as"></a>operator =

```cpp
nested_exception& operator=(const nested_exception&) = default;
```

### <a name="nested_ptr"></a>nested_ptr

```cpp
exception_ptr nested_ptr() const;
```

#### <a name="return-value"></a>Wartość zwracana

Przechowywany wyjątek przechwytywany przez ten `nested_exception` obiekt.

### <a name="rethrow_nested"></a>rethrow_nested

```cpp
[[noreturn]] void rethrow_nested() const;
```

#### <a name="remarks"></a>Uwagi

Jeśli `nested_ptr()` zwraca wskaźnik o wartości null, wywołuje `std::terminate()`funkcję. W przeciwnym razie zgłasza przechowywany wyjątek przechwytywany przez `*this`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> wyjątku

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Klasa wyjątku](../standard-library/exception-class.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
