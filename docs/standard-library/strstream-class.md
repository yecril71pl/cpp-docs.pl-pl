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
ms.openlocfilehash: 796bf1b3ac41a4b5a6ab5bc16239d50616f554df
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224620"
---
# <a name="strstream-class"></a>strstream — Klasa

Opisuje obiekt, który kontroluje Wstawianie i wyodrębnianie elementów i zakodowanych obiektów przy użyciu buforu strumienia klasy [strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Składnia

```cpp
class strstream : public iostream
```

## <a name="remarks"></a>Uwagi

Obiekt przechowuje obiekt klasy `strstreambuf` .

> [!NOTE]
> Ta klasa jest przestarzała. Zamiast tego Rozważ użycie [stringstream —](../standard-library/sstream-typedefs.md#stringstream) lub [wstringstream —](../standard-library/sstream-typedefs.md#wstringstream) .

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[strstream](#strstream)|Konstruuje obiekt typu `strstream` .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[Funkcja](#freeze)|Powoduje, że bufor strumienia nie jest dostępny za pomocą operacji buforu strumienia.|
|[pcount](#pcount)|Zwraca liczbę elementów, które są zapisywane w kontrolowanej sekwencji.|
|[rdbuf](#rdbuf)|Zwraca wskaźnik do obiektu skojarzonego strumienia `strstreambuf` .|
|[str](#str)|Wywołania [zawieszają](../standard-library/strstreambuf-class.md#freeze)się, a następnie zwracają wskaźnik do początku kontrolowanej sekwencji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<strstream>

**Przestrzeń nazw:** std

## <a name="strstreamfreeze"></a><a name="freeze"></a>strstream:: Zablokuj

Powoduje, że bufor strumienia nie jest dostępny za pomocą operacji buforu strumienia.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parametry

*_Freezeit*\
**`bool`** Wskazuje, czy strumień ma być zablokowany.

### <a name="remarks"></a>Uwagi

Funkcja członkowska wywołuje [rdbuf](#rdbuf)  ->  [Zablokuj](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*).

### <a name="example"></a>Przykład

Zobacz [strstreambuf:: Zablokuj](../standard-library/strstreambuf-class.md#freeze) , aby zapoznać się z przykładem, który używa `freeze` .

## <a name="strstreampcount"></a><a name="pcount"></a>strstream: liczba:p

Zwraca liczbę elementów, które są zapisywane w kontrolowanej sekwencji.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów zapisywana w kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [rdbuf](#rdbuf)  ->  [pcount](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Przykład

Zobacz [strstreambuf::p Count](../standard-library/strstreambuf-class.md#pcount) , aby uzyskać przykład użycia pcount.

## <a name="strstreamrdbuf"></a><a name="rdbuf"></a>strstream:: rdbuf

Zwraca wskaźnik do obiektu strstreambuf skojarzonego ze strumieniem.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu strstreambuf skojarzonego ze strumieniem.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca adres bufora zapisanego strumienia typu `pointer` do [strstreambuf](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Przykład

Zobacz [strstreambuf: liczba:p](../standard-library/strstreambuf-class.md#pcount) dla przykładu, który używa `rdbuf` .

## <a name="strstreamstr"></a><a name="str"></a>strstream:: str

Wywołania [zawieszają](../standard-library/strstreambuf-class.md#freeze)się, a następnie zwracają wskaźnik do początku kontrolowanej sekwencji.

```cpp
char *str();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [rdbuf](#rdbuf)  ->  [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Przykład

Zobacz [strstreambuf:: str](../standard-library/strstreambuf-class.md#str) , aby uzyskać przykład, który używa `str` .

## <a name="strstreamstrstream"></a><a name="strstream"></a>strstream:: strstream

Konstruuje obiekt typu `strstream` .

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

Oba konstruktory inicjują klasę bazową przez wywołanie [streambuf](../standard-library/streambuf-typedefs.md#streambuf)( **SB**), gdzie `sb` jest przechowywany obiekt klasy [strstreambuf](../standard-library/strstreambuf-class.md). Pierwszy Konstruktor jest również inicjowany `sb` przez wywołanie [strstreambuf](../standard-library/strstreambuf-class.md#strstreambuf). Drugi Konstruktor inicjuje klasę bazową jeden z dwóch sposobów:

- Jeśli `_Mode`  &  **ios_base:: App**= = 0, wówczas *PTR* musi wyznaczyć pierwszy element tablicy `count` elementów, a Konstruktor wywołuje `strstreambuf` ( `ptr` , `count` , `ptr` ).

- W przeciwnym razie *PTR* musi wyznaczyć pierwszy element tablicy elementów count, który zawiera ciąg C, którego pierwszy element jest wyznaczony przez *PTR*, a Konstruktor wywołuje `strstreambuf` ( `ptr` , `count` , `ptr`  +  `strlen` ( `ptr` )).

## <a name="see-also"></a>Zobacz także

[iostream](../standard-library/istream-typedefs.md#iostream)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostreams](../standard-library/iostreams-conventions.md)
