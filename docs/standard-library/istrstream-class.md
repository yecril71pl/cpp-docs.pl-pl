---
title: istrstream — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- strstream/std::istrstream::rdbuf
- strstream/std::istrstream::str
dev_langs:
- C++
helpviewer_keywords:
- istrstream class
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d6be9c5d9a305032a61677c820832a76c464db4c
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="istrstream-class"></a>istrstream — Klasa

Zawiera opis obiektu, który kontroluje wyodrębniania elementów i zakodowanego obiektów z buforu strumienia klasy [strstreambuf —](../standard-library/strstreambuf-class.md).

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

|Funkcja członkowska|Opis|
|-|-|
|[rdbuf](#rdbuf)|Zwraca wskaźnik do strumienia powiązanych `strstreambuf` obiektu.|
|[str](#str)|Wywołania [Zablokuj](../standard-library/strstreambuf-class.md#freeze), a następnie zwraca wskaźnik do początku kontrolowanej sekwencji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<strstream — >

**Namespace:** Standard

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

`count` Długość buforu ( `ptr`).

`ptr` Zawartość, z których bufor jest inicjowana.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory zainicjowanie klasy głównej przez wywołanie metody [istream](../standard-library/istream-typedefs.md#istream)( **sb**), gdzie **sb** jest przechowywane obiekt klasy [strstreambuf —](../standard-library/strstreambuf-class.md) . Pierwsze dwa konstruktory również zainicjować **sb** przez wywołanie metody `strstreambuf`(( **const** `char` \*) `ptr`, 0). Zamiast tego wywołać pozostałe dwa konstruktory `strstreambuf`(( **const** `char` *) `ptr`, `count` ).

## <a name="rdbuf"></a>  istrstream::rdbuf

Zwraca wskaźnik do obiektu skojarzone strstreambuf — strumienia.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do strumienia powiązanych strstreambuf — obiektu.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca adres buforu przechowywanych strumienia, typu wskaźnika do [strstreambuf —](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Przykład

Zobacz [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) dla przykładu korzystającego z `rdbuf`.

## <a name="str"></a>  istrstream::str

Wywołania [Zablokuj](../standard-library/strstreambuf-class.md#freeze), a następnie zwraca wskaźnik do początku kontrolowanej sekwencji.

```cpp
char *str();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Przykład

Zobacz [strstream::str](../standard-library/strstreambuf-class.md#str) dla przykładu korzystającego z **str**.

## <a name="see-also"></a>Zobacz także

[istream](../standard-library/istream-typedefs.md#istream)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
