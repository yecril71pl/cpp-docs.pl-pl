---
title: istrstream — Klasa
ms.date: 11/04/2016
f1_keywords:
- strstream/std::istrstream::rdbuf
- strstream/std::istrstream::str
helpviewer_keywords:
- istrstream class
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
ms.openlocfilehash: 59b69d3f862715840e1557a10d6087350488a3c9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448074"
---
# <a name="istrstream-class"></a>istrstream — Klasa

Opisuje obiekt, który kontroluje wyodrębnianie elementów i zakodowanych obiektów z bufora strumienia klasy [strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Składnia

```cpp
class istrstream : public istream
```

## <a name="remarks"></a>Uwagi

Obiekt przechowuje obiekt klasy `strstreambuf`.

> [!NOTE]
> Ta klasa jest przestarzała. Zamiast tego Rozważ użycie [istringstream —](../standard-library/sstream-typedefs.md#istringstream) lub [wistringstream —](../standard-library/sstream-typedefs.md#wistringstream) .

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[istrstream](#istrstream)|Konstruuje obiekt typu `istrstream`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[rdbuf](#rdbuf)|Zwraca wskaźnik do obiektu skojarzonego `strstreambuf` strumienia.|
|[str](#str)|Wywołania [zawieszają](../standard-library/strstreambuf-class.md#freeze)się, a następnie zwracają wskaźnik do początku kontrolowanej sekwencji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<strstream >

**Przestrzeń nazw:** std

## <a name="istrstream"></a>istrstream:: istrstream

Konstruuje obiekt typu `istrstream`.

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

Wszystkie konstruktory inicjują klasę bazową przez wywołanie [IStream](../standard-library/istream-typedefs.md#istream)(**SB**), `sb` gdzie jest przechowywany obiekt klasy [strstreambuf](../standard-library/strstreambuf-class.md). Pierwsze dwa konstruktory są również `sb` inicjowane `strstreambuf`przez wywołanie (( `ptr` **const** `char` \*), 0). Pozostałe dwa konstruktory zamiast wywołania `strstreambuf`(( **const** `char` *) `ptr`, `count` ).

## <a name="rdbuf"></a>istrstream:: rdbuf

Zwraca wskaźnik do obiektu strstreambuf skojarzonego ze strumieniem.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu strstreambuf skojarzonego ze strumieniem.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca adres przechowywanego bufora strumienia, typu wskaźnika do [strstreambuf](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Przykład

Zobacz [strstreambuf: liczba:p](../standard-library/strstreambuf-class.md#pcount) dla przykładu, który `rdbuf`używa.

## <a name="str"></a>istrstream:: str

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

[istream](../standard-library/istream-typedefs.md#istream)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
