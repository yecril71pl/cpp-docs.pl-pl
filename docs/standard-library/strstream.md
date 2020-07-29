---
title: '&lt;strstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <strstream>
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
ms.openlocfilehash: a7df541049aafd191e969eaa392ab3706f171926
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224607"
---
# <a name="ltstrstreamgt"></a>&lt;strstream&gt;

Definiuje kilka klas, które obsługują operacje iostreams na sekwencjach przechowywanych w przydzielonym tablicy **`char`** obiektu. Takie sekwencje są łatwo konwertowane na ciągi języka C i z nich.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<strstream>

**Przestrzeń nazw:** std

## <a name="remarks"></a>Uwagi

Obiekty typu `strstream` pracują z **`char`** *, które są ciągami języka C. Służy [\<sstream>](../standard-library/sstream.md) do pracy z obiektami typu [basic_string](../standard-library/basic-string-class.md).

> [!NOTE]
> Klasy w programie \<strstream> są przestarzałe. Rozważ użycie klas w \<sstream> zamian.

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|||
|-|-|
|[Klasa strstreambuf](../standard-library/strstreambuf-class.md)|Klasa opisuje bufor strumienia, który kontroluje przekazywanie elementów do i z sekwencji elementów przechowywanych w **`char`** obiekcie array.|
|[Klasa istrstream](../standard-library/istrstream-class.md)|Klasa opisuje obiekt, który kontroluje wyodrębnianie elementów i zakodowanych obiektów z bufora strumienia klasy [strstreambuf](../standard-library/strstreambuf-class.md).|
|[Klasa ostrstream](../standard-library/ostrstream-class.md)|Klasa opisuje obiekt, który kontroluje Wstawianie elementów i zakodowanych obiektów do buforu strumienia klasy [strstreambuf](../standard-library/strstreambuf-class.md).|
|[Klasa strstream](../standard-library/strstream-class.md)|Klasa opisuje obiekt, który kontroluje Wstawianie i wyodrębnianie elementów i zakodowanych obiektów przy użyciu bufora strumienia klasy [strstreambuf](../standard-library/strstreambuf-class.md).|

### <a name="functions"></a>Funkcje

```cpp
void freeze(bool freezefl = true);
char* str();
int pcount();
```

## <a name="see-also"></a>Zobacz także

[\<strstream>](../standard-library/strstream.md)\
[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostreams](../standard-library/iostreams-conventions.md)
