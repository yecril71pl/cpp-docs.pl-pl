---
title: basic_iostream — Klasa
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_iostream
- istream/std::basic_iostream::swap
helpviewer_keywords:
- basic_iostream class
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
ms.openlocfilehash: 190c9aa23493cea67bae44be93fd3fdbdecc4447
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72690006"
---
# <a name="basic_iostream-class"></a>basic_iostream — Klasa

Klasa strumienia, która może wykonywać zarówno dane wejściowe, jak i wyjściowe.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_iostream : public basic_istream<Elem, Tr>,
    public basic_ostream<Elem, Tr>
{
public:
    explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

    virtual ~basic_iostream();

};
```

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje obiekt, który kontroluje wstawienia, poprzez jego klasę bazową [basic_ostream](../standard-library/basic-ostream-class.md) <  `Elem`, `Tr` > i wyodrębniania, za pomocą swojej klasy podstawowej [basic_istream](../standard-library/basic-istream-class.md) <  `Elem`, `Tr` >. Dwa obiekty współużytkują wspólną wirtualną klasę bazową [basic_ios](../standard-library/basic-ios-class.md) <  `Elem`, `Tr` >. Zarządzają one również wspólnym buforem strumieni, z elementami typu `Elem`, których cechy znaku są określane przez klasę `Tr`. Konstruktor inicjuje swoje klasy podstawowe za pomocą `basic_istream` ( **strbuf**) i `basic_ostream` ( **strbuf**).

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_iostream](#basic_iostream)|Utwórz obiekt `basic_iostream`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[wymiany](#swap)|Wymienia zawartość podanego obiektu `basic_iostream` dla zawartości tego obiektu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator =](#op_eq)|Przypisuje wartość określonego obiektu `basic_iostream` do tego obiektu. Jest to przypisanie przenoszenia obejmujące `rvalue`, które nie pozostawia kopii w tle.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<istream >

**Przestrzeń nazw:** std

## <a name="basic_iostream"></a>basic_iostream::basic_iostream

Utwórz obiekt `basic_iostream`.

```cpp
explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

basic_iostream(basic_iostream&& right);

basic_iostream();
```

### <a name="parameters"></a>Parametry

*strbuf* \
Istniejący obiekt `basic_streambuf`.

*prawa* \
Istniejący obiekt `basic_iostream`, który jest używany do konstruowania nowych `basic_iostream`.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje obiekty podstawowe w sposób `basic_istream(strbuf)` i `basic_ostream(strbuf)`.

Drugi Konstruktor inicjuje obiekty podstawowe przez wywołanie `move(right)`.

## <a name="op_eq"></a>basic_iostream:: operator =

Przypisz wartość określonego obiektu `basic_iostream` do tego obiektu. Jest to przypisanie przenoszenia obejmujące rvalue, które nie pozostawia kopii w tle.

```cpp
basic_iostream& operator=(basic_iostream&& right);
```

### <a name="parameters"></a>Parametry

*prawa* \
Odwołanie `rvalue` do obiektu `basic_iostream`, z którego ma zostać przypisane przypisanie.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego wywołuje `swap(right)`.

## <a name="swap"></a>basic_iostream:: swap

Wymienia zawartość podanego obiektu `basic_iostream` dla zawartości tego obiektu.

```cpp
void swap(basic_iostream& right);
```

### <a name="parameters"></a>Parametry

*prawa* \
Obiekt `basic_iostream` do zamiany.

### <a name="remarks"></a>Uwagi

Funkcja członkowska wywołuje `swap(right)`.

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
\ [programowania iostream](../standard-library/iostream-programming.md)
[Konwencje iostream](../standard-library/iostreams-conventions.md)
