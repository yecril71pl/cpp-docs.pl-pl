---
title: Klasa nested_exception
ms.date: 11/04/2016
f1_keywords:
- exception/std::nested_exception
helpviewer_keywords:
- nested_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: ed58eb6cc074b54ae6801d2b11089af9a79f8c8f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441615"
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

### <a name="op_as"></a>operator =

```cpp
nested_exception& operator=(const nested_exception&) = default;
```

### <a name="nested_ptr"></a>nested_ptr

```cpp
exception_ptr nested_ptr() const;
```

#### <a name="return-value"></a>Wartość zwrócona

Zapisany wyjątek przechwytywany przez ten obiekt `nested_exception`.

### <a name="rethrow_nested"></a>rethrow_nested

```cpp
[[noreturn]] void rethrow_nested() const;
```

#### <a name="remarks"></a>Uwagi

Jeśli `nested_ptr()` zwraca wskaźnik o wartości null, funkcja wywołuje `std::terminate()`. W przeciwnym razie zgłasza wyjątek przechowywany przez `*this`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wyjątek >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz też

\ [klasy wyjątku](../standard-library/exception-class.md)
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
