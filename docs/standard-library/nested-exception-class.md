---
title: nested_exception klasy
ms.date: 11/04/2016
f1_keywords:
- exception/std::bad_exception
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: a568a8d9a3817883656406d63c3dd948539bb385
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68267911"
---
# <a name="nestedexception-class"></a>nested_exception klasy

Klasa opisuje wyjątek do użycia z wielokrotnego dziedziczenia. Jego przechwytuje aktualnie obsługiwany wyjątek i zapisuje go do późniejszego użycia.

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
|[rethrow_nested](#rethrow_nested)|Wyjątek przechowywanych.|
|[nested_ptr](#nested_ptr)|Zwraca przechowywaną wyjątku.|

### <a name="op_as"></a> operator =

```cpp
nested_exception& operator=(const nested_exception&) = default;
```

### <a name="nested_ptr"></a> nested_ptr

```cpp
exception_ptr nested_ptr() const;
```

#### <a name="return-value"></a>Wartość zwracana

Przechowywane wyjątek przechwycony przez to `nested_exception` obiektu.

### <a name="rethrow_nested"></a> rethrow_nested

```cpp
[[noreturn]] void rethrow_nested() const;
```

#### <a name="remarks"></a>Uwagi

Jeśli `nested_ptr()` zwraca wskaźnikiem typu null, wywołania funkcji `std::terminate()`. W przeciwnym razie wyniku weryfikacji zgłasza wyjątek przechowywanych wyjątek przechwycony przez `*this`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wyjątku >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[exception, klasa](../standard-library/exception-class.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
