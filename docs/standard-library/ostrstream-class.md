---
title: ostrstream — Klasa
ms.date: 11/04/2016
f1_keywords:
- strstream/std::ostrstream::freeze
- strstream/std::ostrstream::pcount
- strstream/std::ostrstream::rdbuf
- strstream/std::ostrstream::str
helpviewer_keywords:
- std::ostrstream [C++], freeze
- std::ostrstream [C++], pcount
- std::ostrstream [C++], rdbuf
- std::ostrstream [C++], str
ms.assetid: e2e34679-b266-4728-a8e1-8eda5d400e46
ms.openlocfilehash: c73ab13d3cb2531ff3d741766bc86f8354a0be9d
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458063"
---
# <a name="ostrstream-class"></a>ostrstream — Klasa

Opisuje obiekt, który kontroluje Wstawianie elementów i zakodowanych obiektów do buforu strumienia klasy [strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Składnia

```cpp
class ostrstream : public ostream
```

## <a name="remarks"></a>Uwagi

Obiekt przechowuje obiekt klasy `strstreambuf`.

> [!NOTE]
> Ta klasa jest przestarzała. Zamiast tego Rozważ użycie [ostringstream —](../standard-library/sstream-typedefs.md#ostringstream) lub [wostringstream —](../standard-library/sstream-typedefs.md#wostringstream) .

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[ostrstream](#ostrstream)|Konstruuje obiekt typu `ostrstream`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[Funkcja](#freeze)|Powoduje, że bufor strumienia nie jest dostępny za pomocą operacji buforu strumienia.|
|[pcount](#pcount)|Zwraca liczbę elementów, które są zapisywane w kontrolowanej sekwencji.|
|[rdbuf](#rdbuf)|Zwraca wskaźnik do obiektu skojarzonego `strstreambuf` strumienia.|
|[str](#str)|Wywołania [zawieszają](../standard-library/strstreambuf-class.md#freeze)się, a następnie zwracają wskaźnik do początku kontrolowanej sekwencji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<strstream >

**Przestrzeń nazw:** std

## <a name="freeze"></a>ostrstream:: Zablokuj

Powoduje, że bufor strumienia nie jest dostępny za pomocą operacji buforu strumienia.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parametry

*_Freezeit*\
Wartość **logiczna** wskazująca, czy strumień ma być zablokowany.

### <a name="remarks"></a>Uwagi

Funkcja członkowska wywołuje [rdbuf](#rdbuf) -> Zablokuj (_ *Freezeit*).[](../standard-library/strstreambuf-class.md#freeze)

### <a name="example"></a>Przykład

Zobacz [strstream::](../standard-library/strstreambuf-class.md#freeze) Zablokuj, aby zapoznać `freeze`się z przykładem, który używa.

## <a name="ostrstream"></a>ostrstream:: ostrstream

Konstruuje obiekt typu `ostrstream`.

```cpp
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Parametry

*PTR*\
Bufor.

*liczbą*\
Rozmiar buforu w bajtach.

*_Mode*\
Tryb wejścia i wyjścia bufora. Aby uzyskać więcej informacji, zobacz [ios_base:: openmode](../standard-library/ios-base-class.md#openmode) .

### <a name="remarks"></a>Uwagi

Oba konstruktory inicjują klasę bazową przez wywołanie [ostream](../standard-library/ostream-typedefs.md#ostream)(**SB**) `sb` , gdzie jest przechowywany obiekt klasy [strstreambuf](../standard-library/strstreambuf-class.md). Pierwszy Konstruktor jest również inicjowany `sb` przez wywołanie. `strstreambuf` Drugi Konstruktor inicjuje klasę bazową jeden z dwóch sposobów:

- Jeśli `_Mode` `strstreambuf` `count` `count`  `ptr` `ptr`ios_base:: App = = 0, a następnie musi wyznaczyć pierwszy element tablicy elementów, a Konstruktor wywołuje (,,  &  `ptr`).

- `ptr` `ptr` `strstreambuf`W przeciwnym razie `count`należy wyznaczyć pierwszy element tablicy elementów count, który zawiera ciąg C, którego pierwszy element jest wyznaczony przez, i Konstruktor wywołuje (,, `ptr` `ptr` + `strlen`( `ptr`) ).

## <a name="pcount"></a>ostrstream: liczba:p

Zwraca liczbę elementów, które są zapisywane w kontrolowanej sekwencji.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów zapisywana w kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Przykład

Zobacz [strstream: liczba:p](../standard-library/strstreambuf-class.md#pcount) dla przykładu, który `pcount`używa.

## <a name="rdbuf"></a>ostrstream:: rdbuf

Zwraca wskaźnik do obiektu strstreambuf skojarzonego ze strumieniem.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu strstreambuf skojarzonego ze strumieniem.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca adres bufora zapisanego strumienia typu `pointer` do [strstreambuf](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Przykład

Zobacz [strstreambuf: liczba:p](../standard-library/strstreambuf-class.md#pcount) dla przykładu, który `rdbuf`używa.

## <a name="str"></a>ostrstream:: str

Wywołania [zawieszają](../standard-library/strstreambuf-class.md#freeze)się, a następnie zwracają wskaźnik do początku kontrolowanej sekwencji.

```cpp
char *str();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Przykład

Zobacz [strstream:: str](../standard-library/strstreambuf-class.md#str) , aby uzyskać przykład, `str`który używa.

## <a name="see-also"></a>Zobacz także

[ostream](../standard-library/ostream-typedefs.md#ostream)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
