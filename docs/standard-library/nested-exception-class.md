---
title: Klasa nested_exception
ms.date: 11/04/2016
f1_keywords:
- exception/std::nested_exception
helpviewer_keywords:
- nested_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: 6ae95880f0bc18928ed9bd4f6b6da14722f6ec60
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212192"
---
# <a name="nested_exception-class"></a>Klasa nested_exception

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
|[operator =](#op_as)||

### <a name="functions"></a>Funkcje

|||
|-|-|
|[rethrow_nested](#rethrow_nested)|Zgłasza wyjątek przechowywany.|
|[nested_ptr](#nested_ptr)|Zwraca przechowywany wyjątek.|

### <a name="operator"></a><a name="op_as"></a>operator =

```cpp
nested_exception& operator=(const nested_exception&) = default;
```

### <a name="nested_ptr"></a><a name="nested_ptr"></a>nested_ptr

```cpp
exception_ptr nested_ptr() const;
```

#### <a name="return-value"></a>Wartość zwracana

Przechowywany wyjątek przechwytywany przez ten `nested_exception` obiekt.

### <a name="rethrow_nested"></a><a name="rethrow_nested"></a>rethrow_nested

```cpp
[[noreturn]] void rethrow_nested() const;
```

#### <a name="remarks"></a>Uwagi

Jeśli `nested_ptr()` zwraca wskaźnik o wartości null, wywołuje funkcję `std::terminate()` . W przeciwnym razie zgłasza przechowywany wyjątek przechwytywany przez **`*this`** .

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<exception>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Klasa wyjątku](../standard-library/exception-class.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
