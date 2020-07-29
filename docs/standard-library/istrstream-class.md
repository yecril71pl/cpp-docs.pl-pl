---
title: istrstream — Klasa
ms.date: 11/04/2016
f1_keywords:
- strstream/std::istrstream::rdbuf
- strstream/std::istrstream::str
helpviewer_keywords:
- istrstream class
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
ms.openlocfilehash: 37118772f7cefd6f380ceb01908da55500ee7ab5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228235"
---
# <a name="istrstream-class"></a>istrstream — Klasa

Opisuje obiekt, który kontroluje wyodrębnianie elementów i zakodowanych obiektów z bufora strumienia klasy [strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Składnia

```cpp
class istrstream : public istream
```

## <a name="remarks"></a>Uwagi

Obiekt przechowuje obiekt klasy `strstreambuf` .

> [!NOTE]
> Ta klasa jest przestarzała. Zamiast tego Rozważ użycie [istringstream —](../standard-library/sstream-typedefs.md#istringstream) lub [wistringstream —](../standard-library/sstream-typedefs.md#wistringstream) .

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[istrstream](#istrstream)|Konstruuje obiekt typu `istrstream` .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[rdbuf](#rdbuf)|Zwraca wskaźnik do obiektu skojarzonego strumienia `strstreambuf` .|
|[str](#str)|Wywołania [zawieszają](../standard-library/strstreambuf-class.md#freeze)się, a następnie zwracają wskaźnik do początku kontrolowanej sekwencji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<strstream>

**Przestrzeń nazw:** std

## <a name="istrstreamistrstream"></a><a name="istrstream"></a>istrstream:: istrstream

Konstruuje obiekt typu `istrstream` .

```cpp
explicit istrstream(
    const char* ptr);

explicit istrstream(
    char* ptr);

istrstream(
    const char* ptr,
    streamsize count);

istrstream(
    char* ptr,
    int count);
```

### <a name="parameters"></a>Parametry

*liczbą*\
Długość buforu (*PTR*).

*PTR*\
Zawartość, z którą został zainicjowany bufor.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory inicjują klasę bazową przez wywołanie [IStream](../standard-library/istream-typedefs.md#istream)(**SB**), gdzie `sb` jest przechowywany obiekt klasy [strstreambuf](../standard-library/strstreambuf-class.md). Dwa pierwsze konstruktory są również inicjowane `sb` przez wywołanie `strstreambuf( ( const char *) ptr, 0 )` . Pozostałe dwa konstruktory zamiast wywołania `strstreambuf( ( const char *) ptr, count )` .

## <a name="istrstreamrdbuf"></a><a name="rdbuf"></a>istrstream:: rdbuf

Zwraca wskaźnik do obiektu strstreambuf skojarzonego ze strumieniem.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu strstreambuf skojarzonego ze strumieniem.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca adres przechowywanego bufora strumienia, typu wskaźnika do [strstreambuf](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Przykład

Zobacz [strstreambuf: liczba:p](../standard-library/strstreambuf-class.md#pcount) dla przykładu, który używa `rdbuf` .

## <a name="istrstreamstr"></a><a name="str"></a>istrstream:: str

Wywołania [zawieszają](../standard-library/strstreambuf-class.md#freeze)się, a następnie zwracają wskaźnik do początku kontrolowanej sekwencji.

```cpp
char *str();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [rdbuf](#rdbuf)  ->  [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Przykład

Zobacz [strstream:: str](../standard-library/strstreambuf-class.md#str) , aby uzyskać przykład, który używa `str` .

## <a name="see-also"></a>Zobacz także

[IStream](../standard-library/istream-typedefs.md#istream)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostreams](../standard-library/iostreams-conventions.md)
