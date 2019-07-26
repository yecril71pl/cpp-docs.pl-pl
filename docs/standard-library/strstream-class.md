---
title: strstream — Klasa
ms.date: 11/04/2016
f1_keywords:
- strstream/std::strstream::freeze
- strstream/std::strstream::pcount
- strstream/std::strstream::rdbuf
- strstream/std::strstream::str
helpviewer_keywords:
- std::strstream [C++], freeze
- std::strstream [C++], pcount
- std::strstream [C++], rdbuf
- std::strstream [C++], str
ms.assetid: 63f3be31-9e36-42b1-9715-a474a5997e2a
ms.openlocfilehash: 53baa350121796d5198211e1fdb08f4341df6b80
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459103"
---
# <a name="strstream-class"></a>strstream — Klasa

Opisuje obiekt, który kontroluje Wstawianie i wyodrębnianie elementów i zakodowanych obiektów przy użyciu buforu strumienia klasy [strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Składnia

```cpp
class strstream : public iostream
```

## <a name="remarks"></a>Uwagi

Obiekt przechowuje obiekt klasy `strstreambuf`.

> [!NOTE]
> Ta klasa jest przestarzała. Zamiast tego Rozważ użycie [stringstream —](../standard-library/sstream-typedefs.md#stringstream) lub [wstringstream —](../standard-library/sstream-typedefs.md#wstringstream) .

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[strstream](#strstream)|Konstruuje obiekt typu `strstream`.|

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

## <a name="freeze"></a>strstream:: Zablokuj

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

Zobacz [strstreambuf::](../standard-library/strstreambuf-class.md#freeze) Zablokuj, aby zapoznać `freeze`się z przykładem, który używa.

## <a name="pcount"></a>strstream: liczba:p

Zwraca liczbę elementów, które są zapisywane w kontrolowanej sekwencji.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów zapisywana w kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Przykład

Zobacz [strstreambuf::p Count](../standard-library/strstreambuf-class.md#pcount) , aby uzyskać przykład użycia pcount.

## <a name="rdbuf"></a>strstream:: rdbuf

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

## <a name="str"></a>strstream:: str

Wywołania [zawieszają](../standard-library/strstreambuf-class.md#freeze)się, a następnie zwracają wskaźnik do początku kontrolowanej sekwencji.

```cpp
char *str();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Przykład

Zobacz [strstreambuf:: str](../standard-library/strstreambuf-class.md#str) , aby uzyskać przykład, `str`który używa.

## <a name="strstream"></a>strstream:: strstream

Konstruuje obiekt typu `strstream`.

```cpp
strstream();

strstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*liczbą*\
Rozmiar buforu.

*_Mode*\
Tryb wejścia i wyjścia bufora. Aby uzyskać więcej informacji, zobacz [ios_base:: openmode](../standard-library/ios-base-class.md#openmode) .

*PTR*\
Bufor.

### <a name="remarks"></a>Uwagi

Oba konstruktory inicjują klasę bazową przez wywołanie [streambuf](../standard-library/streambuf-typedefs.md#streambuf)( **SB**) `sb` , gdzie jest przechowywany obiekt klasy [strstreambuf](../standard-library/strstreambuf-class.md). Pierwszy Konstruktor jest również inicjowany `sb` przez wywołanie [strstreambuf](../standard-library/strstreambuf-class.md#strstreambuf). Drugi Konstruktor inicjuje klasę bazową jeden z dwóch sposobów:

- Jeśli `_Mode` `strstreambuf` `ptr` `count` `count` `ptr`  ios_base:: App = = 0, wówczas PTR musi wyznaczyć pierwszy element tablicy elementów, a Konstruktor wywołuje (,,)  &  .

- W przeciwnym *razie PTR* musi wyznaczyć pierwszy element tablicy elementów count, który zawiera ciąg C, którego pierwszy element jest wyznaczony przez *PTR*, a Konstruktor wywołuje `strstreambuf`( `ptr`, `count`, `ptr`  +  `strlen`( `ptr`) ).

## <a name="see-also"></a>Zobacz także

[iostream](../standard-library/istream-typedefs.md#iostream)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
