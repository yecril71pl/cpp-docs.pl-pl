---
title: istrstream — Klasa
ms.date: 11/04/2016
f1_keywords:
- strstream/std::istrstream::rdbuf
- strstream/std::istrstream::str
helpviewer_keywords:
- istrstream class
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
ms.openlocfilehash: d548a8c2c47a5a345be725afdedb47524344f720
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337525"
---
# <a name="istrstream-class"></a>istrstream — Klasa

W tym artykule opisano obiekt, który kontroluje wyodrębnianie elementów i zakodowanych obiektów z buforu strumienia [klasy strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Składnia

```cpp
class istrstream : public istream
```

## <a name="remarks"></a>Uwagi

Obiekt przechowuje obiekt `strstreambuf`klasy .

> [!NOTE]
> Ta klasa jest przestarzała. Należy rozważyć użycie [istringstream](../standard-library/sstream-typedefs.md#istringstream) lub [wistringstream](../standard-library/sstream-typedefs.md#wistringstream) zamiast.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[strumień istrstream](#istrstream)|Konstruuje obiekt `istrstream`typu .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Rdbuf](#rdbuf)|Zwraca wskaźnik do skojarzonego z `strstreambuf` nim obiektu strumienia.|
|[Str](#str)|Wywołania [freeze](../standard-library/strstreambuf-class.md#freeze), a następnie zwraca wskaźnik na początku kontrolowanej sekwencji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<strstream>

**Przestrzeń nazw:** std

## <a name="istrstreamistrstream"></a><a name="istrstream"></a>istrstream::istrstream

Konstruuje obiekt `istrstream`typu .

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

*Liczba*\
Długość buforu (*ptr*).

*Ptr*\
Zawartość, z którą bufor jest inicjowany.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory inicjują klasę podstawową, `sb` wywołując [istream](../standard-library/istream-typedefs.md#istream)**(sb),** gdzie jest przechowywanym obiektem klasy [strstreambuf](../standard-library/strstreambuf-class.md). Pierwsze dwa konstruktory `sb` również `strstreambuf`inicjować `ptr`przez wywołanie ( ( **const** `char` \*), 0 ). Pozostałe dwa konstruktory `strstreambuf`zamiast wywołać `ptr`( `count` ( **const** `char` *) , ).

## <a name="istrstreamrdbuf"></a><a name="rdbuf"></a>istrstream::rdbuf

Zwraca wskaźnik do skojarzonego strumienia strstreambuf obiektu.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu strstreambuf skojarzonego strumienia.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca adres przechowywanego buforu strumienia, wskaźnik typu do [strstreambuf](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Przykład

Zobacz [strstreambuf::plice](../standard-library/strstreambuf-class.md#pcount) dla próbki, która `rdbuf`używa .

## <a name="istrstreamstr"></a><a name="str"></a>istrstream::str

Wywołania [freeze](../standard-library/strstreambuf-class.md#freeze), a następnie zwraca wskaźnik na początku kontrolowanej sekwencji.

```cpp
char *str();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Przykład

Zobacz [strstream::str](../standard-library/strstreambuf-class.md#str) dla próbki, `str`która używa .

## <a name="see-also"></a>Zobacz też

[Istream](../standard-library/istream-typedefs.md#istream)\
[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
