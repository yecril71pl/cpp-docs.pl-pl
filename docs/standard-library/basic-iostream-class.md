---
title: basic_iostream — Klasa
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_iostream
- istream/std::basic_iostream::swap
helpviewer_keywords:
- basic_iostream class
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
ms.openlocfilehash: 052271e2e2cc929875489e27abde2147bc5c070a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460087"
---
# <a name="basiciostream-class"></a>basic_iostream — Klasa

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

Klasa szablonu opisuje obiekt, który kontroluje wstawienia, za pomocą jego klasy bazowej `Tr` [basic_ostream](../standard-library/basic-ostream-class.md)< `Elem`, > i wyodrębniania, za pomocą swojej klasy bazowej [basic_istream](../standard-library/basic-istream-class.md) <  `Elem` ,`Tr`>. Te dwa obiekty współużytkują wspólną wirtualną klasę bazową `Tr` [basic_ios](../standard-library/basic-ios-class.md)< `Elem`>. Zarządzają one również wspólnym buforem strumieni z elementami typu `Elem`, których cechy znaku są określane przez klasę. `Tr` Konstruktor inicjuje swoje klasy podstawowe za pomocą `basic_istream`( **strbuf**) i `basic_ostream`( **strbuf**).

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_iostream](#basic_iostream)|Tworzy obiekt `basic_iostream`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[swap](#swap)|Wymienia zawartość podanego `basic_iostream` obiektu dla zawartości tego obiektu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Przypisuje wartość określonego `basic_iostream` obiektu do tego obiektu. Jest to przypisanie przenoszenia obejmujące element `rvalue` , który nie pozostawia kopii w tle.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<IStream >

**Przestrzeń nazw:** std

## <a name="basic_iostream"></a>basic_iostream::basic_iostream

Tworzy obiekt `basic_iostream`.

```cpp
explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

basic_iostream(basic_iostream&& right);

basic_iostream();
```

### <a name="parameters"></a>Parametry

*strbuf*\
Istniejący `basic_streambuf` obiekt.

*Kliknij*\
Istniejący `basic_iostream` obiekt, który jest używany do utworzenia nowego `basic_iostream`.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje obiekty podstawowe w `basic_istream(strbuf)` drodze do i. `basic_ostream(strbuf)`

Drugi Konstruktor inicjuje obiekty podstawowe przez wywołanie `move(right)`.

## <a name="op_eq"></a>basic_iostream:: operator =

Przypisz wartość określonego `basic_iostream` obiektu do tego obiektu. Jest to przypisanie przenoszenia obejmujące rvalue, które nie pozostawia kopii w tle.

```cpp
basic_iostream& operator=(basic_iostream&& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Odwołanie do obiektu, `basic_iostream` z którego ma zostać przypisane przypisanie. `rvalue`

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego `swap(right)`wywołuje.

## <a name="swap"></a>basic_iostream:: swap

Wymienia zawartość podanego `basic_iostream` obiektu dla zawartości tego obiektu.

```cpp
void swap(basic_iostream& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
`basic_iostream` Obiekt do zamiany.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego `swap(right)`wywołuje.

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
