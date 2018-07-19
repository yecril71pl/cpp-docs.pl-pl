---
title: istrstream — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- strstream/std::istrstream::rdbuf
- strstream/std::istrstream::str
dev_langs:
- C++
helpviewer_keywords:
- istrstream class
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6484d70488da834d0acea79cbe9b02968e0e2a35
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957288"
---
# <a name="istrstream-class"></a>istrstream — Klasa

Opisuje obiekt, który kontroluje wyodrębniania elementów i zakodowany obiektów z bufor strumienia klasy [strstreambuf —](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Składnia

```cpp
class istrstream : public istream
```

## <a name="remarks"></a>Uwagi

Obiekt przechowuje obiekt klasy `strstreambuf`.

> [!NOTE]
> Ta klasa jest przestarzały. Należy rozważyć użycie [istringstream](../standard-library/sstream-typedefs.md#istringstream) lub [wistringstream](../standard-library/sstream-typedefs.md#wistringstream) zamiast tego.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[istrstream](#istrstream)|Tworzy obiekt typu `istrstream`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[rdbuf](#rdbuf)|Zwraca wskaźnik do strumienia skojarzonej `strstreambuf` obiektu.|
|[str](#str)|Wywołania [freeze](../standard-library/strstreambuf-class.md#freeze), a następnie zwraca wskaźnik do początku kontrolowanej sekwencji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<strstream — >

**Namespace:** standardowe

## <a name="istrstream"></a>  istrstream::istrstream

Tworzy obiekt typu `istrstream`.

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

*Liczba* długość buforu (*ptr*).

*PTR* zawartość za pomocą których rozmiar buforu jest zainicjowany.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory inicjowania klasy bazowej, wywołując [istream](../standard-library/istream-typedefs.md#istream)(**sb**), gdzie `sb` jest przechowywany obiekt klasy [strstreambuf —](../standard-library/strstreambuf-class.md). Dwa pierwsze konstruktory również inicjują `sb` przez wywołanie metody `strstreambuf`(( **const** `char` \*) `ptr`, 0). Zamiast tego wywoływać pozostałe dwa konstruktory `strstreambuf`(( **const** `char` *) `ptr`, `count` ).

## <a name="rdbuf"></a>  istrstream::rdbuf

Zwraca wskaźnik do obiektu skojarzone strstreambuf — strumienia.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Wartość zwracana

Strstreambuf — obiekt skojarzonej wskaźnik do strumienia.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca adres bufor strumienia przechowywane, typu wskaźnika do [strstreambuf —](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Przykład

Zobacz [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) dla przykładu, który używa `rdbuf`.

## <a name="str"></a>  istrstream::str

Wywołania [freeze](../standard-library/strstreambuf-class.md#freeze), a następnie zwraca wskaźnik do początku kontrolowanej sekwencji.

```cpp
char *str();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik na początek kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [rdbuf —](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Przykład

Zobacz [strstream::str](../standard-library/strstreambuf-class.md#str) dla przykładu, który używa `str`.

## <a name="see-also"></a>Zobacz także

[istream](../standard-library/istream-typedefs.md#istream)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
