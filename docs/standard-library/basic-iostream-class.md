---
title: basic_iostream — Klasa
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_iostream
- istream/std::basic_iostream::swap
helpviewer_keywords:
- basic_iostream class
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
ms.openlocfilehash: 80aad69f05b7473b508447d6f69f1d92edbeeca3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400646"
---
# <a name="basiciostream-class"></a>basic_iostream — Klasa

Klasa strumienia, która może wykonać obie czynności danych wejściowych i wyjściowych.

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

Klasa szablonu opisuje obiekt, który kontroluje za pośrednictwem jej klasa podstawowa liczba operacji wstawienia [basic_ostream](../standard-library/basic-ostream-class.md)< `Elem`, `Tr`> i wyodrębniania za pośrednictwem swojej klasy bazowej [basic_ IStream](../standard-library/basic-istream-class.md)< `Elem`, `Tr`>. Dwa obiekty współużytkują wspólne wirtualnej klasy bazowej [basic_ios —](../standard-library/basic-ios-class.md)< `Elem`, `Tr`>. Również zarządzać wspólnej bufora strumienia, elementami typu `Elem`, którego cech są określane przez klasę `Tr`. Konstruktor inicjuje jego klas podstawowych za pośrednictwem `basic_istream`( **strbuf**) i `basic_ostream`( **strbuf**).

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_iostream](#basic_iostream)|Tworzy obiekt `basic_iostream`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[swap](#swap)|Wymienia zawartość dostarczonego `basic_iostream` obiektu dla zawartości tego obiektu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Przypisuje wartość określonego `basic_iostream` obiektu do tego obiektu. Jest to przeniesienia przypisania obejmujące `rvalue` , nie pozostawione kopię.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<istream >

**Namespace:** standardowe

## <a name="basic_iostream"></a>  basic_iostream::basic_iostream

Tworzy obiekt `basic_iostream`.

```cpp
explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

basic_iostream(basic_iostream&& right);

basic_iostream();
```

### <a name="parameters"></a>Parametry

*strbuf*<br/>
Istniejące `basic_streambuf` obiektu.

*right*<br/>
Istniejące `basic_iostream` obiekt, który jest używany do tworzenia nowego `basic_iostream`.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje obiektów podstawowych za `basic_istream(strbuf)` i `basic_ostream(strbuf)`.

Drugi Konstruktor inicjuje obiekty podstawowe, wywołując `move(right)`.

## <a name="op_eq"></a>  basic_iostream::operator =

Przypisz wartość określonego `basic_iostream` obiektu do tego obiektu. Jest to przeniesienia przypisania obejmujące rvalue, który nie pozostawione kopię.

```cpp
basic_iostream& operator=(basic_iostream&& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
`rvalue` Odwołanie do `basic_iostream` obiekt można przypisać z.

### <a name="remarks"></a>Uwagi

Element członkowski wywołuje operator `swap(right)`.

## <a name="swap"></a>  basic_iostream::swap

Wymienia zawartość dostarczonego `basic_iostream` obiektu dla zawartości tego obiektu.

```cpp
void swap(basic_iostream& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
`basic_iostream` Obiekt do wymiany.

### <a name="remarks"></a>Uwagi

Wywołania funkcji elementu członkowskiego `swap(right)`.

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
