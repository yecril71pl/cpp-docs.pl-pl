---
title: basic_iostream — Klasa
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_iostream
- istream/std::basic_iostream::swap
helpviewer_keywords:
- basic_iostream class
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
ms.openlocfilehash: e2a892525afbbad6d5b42d0b836fee096a70c297
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376817"
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

Szablon klasy opisuje obiekt, który steruje wstawieniami `Tr` za pośrednictwem klasy podstawowej [basic_ostream](../standard-library/basic-ostream-class.md)< `Elem`,> i `Tr` ekstrakcji, za pośrednictwem klasy podstawowej [basic_istream](../standard-library/basic-istream-class.md)< `Elem`,>. Dwa obiekty mają wspólną wirtualną klasę `Tr` podstawową [basic_ios](../standard-library/basic-ios-class.md)< `Elem`,>. Zarządzają również wspólnym buforem strumienia, z elementami typu, `Elem` `Tr`których cechy charakteru są określane przez klasę. Konstruktor inicjuje swoje `basic_istream`klasy podstawowe poprzez `basic_ostream`( **strbuf**) i ( **strbuf**).

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_iostream](#basic_iostream)|Utwórz `basic_iostream` obiekt.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Wymiany](#swap)|Wymienia zawartość dostarczonego `basic_iostream` obiektu dla zawartości tego obiektu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Przypisuje wartość określonego `basic_iostream` obiektu do tego obiektu. Jest to przypisanie przenoszenia obejmujące, `rvalue` który nie pozostawia kopię za sobą.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<istream>

**Przestrzeń nazw:** std

## <a name="basic_iostreambasic_iostream"></a><a name="basic_iostream"></a>basic_iostream::basic_iostream

Utwórz `basic_iostream` obiekt.

```cpp
explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

basic_iostream(basic_iostream&& right);

basic_iostream();
```

### <a name="parameters"></a>Parametry

*strbuf*\
Istniejący `basic_streambuf` obiekt.

*Prawo*\
Istniejący `basic_iostream` obiekt, który jest `basic_iostream`używany do konstruowania nowego .

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor inicjuje obiekty `basic_istream(strbuf)` bazowe w drodze i `basic_ostream(strbuf)`.

Drugi konstruktor inicjuje obiekty `move(right)`bazowe, wywołując .

## <a name="basic_iostreamoperator"></a><a name="op_eq"></a>basic_iostream::operator=

Przypisz wartość określonego `basic_iostream` obiektu do tego obiektu. Jest to przypisanie przenoszenia obejmujące wartość r, która nie pozostawia kopii za sobą.

```cpp
basic_iostream& operator=(basic_iostream&& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Odwołanie `rvalue` do `basic_iostream` obiektu do przypisania z.

### <a name="remarks"></a>Uwagi

Operator elementu `swap(right)`członkowskiego wywołuje .

## <a name="basic_iostreamswap"></a><a name="swap"></a>basic_iostream::swap

Wymienia zawartość dostarczonego `basic_iostream` obiektu dla zawartości tego obiektu.

```cpp
void swap(basic_iostream& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Obiekt `basic_iostream` do wymiany.

### <a name="remarks"></a>Uwagi

Funkcja elementu `swap(right)`członkowskiego wywołuje .

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
