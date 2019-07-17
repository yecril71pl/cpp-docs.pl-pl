---
title: '&lt;strstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <strstream>
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
ms.openlocfilehash: 212223f98db09097e596fc6fe2ddd31bbe16e6b7
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245370"
---
# <a name="ltstrstreamgt"></a>&lt;strstream&gt;

Definiuje kilka klas, które obsługują operacje iostreams w sekwencji przechowywane w tablicy przydzielonego **char** obiektu. Takie sekwencje łatwo są konwertowane do i z ciągami C.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<strstream — >

**Namespace:** standardowe

## <a name="remarks"></a>Uwagi

Obiekty typu `strstream` działają z `char` *, które są ciągami C. Użyj [ \<strumienia >](../standard-library/sstream.md) do pracy z obiektami typu [basic_string](../standard-library/basic-string-class.md).

> [!NOTE]
> Klasy w \<strstream — > są przestarzałe. Należy wziąć pod uwagę przy użyciu klas w \<strumienia > zamiast tego.

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|||
|-|-|
|[strstreambuf, klasa](../standard-library/strstreambuf-class.md)|Klasa opisuje buforu strumieni, który kontroluje przekazywanie elementów do i z sekwencji elementów przechowywanych w **char** obiektu array.|
|[istrstream, klasa](../standard-library/istrstream-class.md)|Klasa opisuje obiekt, który kontroluje wyodrębniania elementów i zakodowany obiektów z bufor strumienia klasy [strstreambuf —](../standard-library/strstreambuf-class.md).|
|[ostrstream, klasa](../standard-library/ostrstream-class.md)|Klasa opisuje obiekt, który kontroluje wstawiania elementów i zakodowany obiekty do bufora strumienia, klasy [strstreambuf —](../standard-library/strstreambuf-class.md).|
|[strstream, klasa](../standard-library/strstream-class.md)|Klasa opisuje obiekt, który kontroluje wstawienia i wydobycia elementów i obiektów zakodowanych przy użyciu bufor strumienia klasy [strstreambuf —](../standard-library/strstreambuf-class.md).|

### <a name="functions"></a>Funkcje

```cpp
void freeze(bool freezefl = true);
char* str();
int pcount();
```

## <a name="see-also"></a>Zobacz także

[\<strstream>](../standard-library/strstream.md)<br/>
[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
