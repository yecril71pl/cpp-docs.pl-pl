---
title: '&lt;strstream —&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <strstream>
dev_langs:
- C++
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1695306ddc53a8150917eef8b27f5d3edce2bf3
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961867"
---
# <a name="ltstrstreamgt"></a>&lt;strstream&gt;

Definiuje kilka klas, które obsługują operacje iostreams w sekwencji przechowywane w tablicy przydzielonego **char** obiektu. Takie sekwencje łatwo są konwertowane do i z ciągami C.

## <a name="syntax"></a>Składnia

```cpp
#include <strstream>

```

## <a name="remarks"></a>Uwagi

Obiekty typu `strstream` działają z `char` *, które są ciągami C. Użyj [ \<strumienia >](../standard-library/sstream.md) do pracy z obiektami typu [basic_string](../standard-library/basic-string-class.md).

> [!NOTE]
> Klasy w \<strstream — > są przestarzałe. Należy wziąć pod uwagę przy użyciu klas w \<strumienia > zamiast tego.

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[strstreambuf, klasa](../standard-library/strstreambuf-class.md)|Klasa opisuje buforu strumieni, który kontroluje przekazywanie elementów do i z sekwencji elementów przechowywanych w **char** obiektu array.|
|[istrstream, klasa](../standard-library/istrstream-class.md)|Klasa opisuje obiekt, który kontroluje wyodrębniania elementów i zakodowany obiektów z bufor strumienia klasy [strstreambuf —](../standard-library/strstreambuf-class.md).|
|[ostrstream, klasa](../standard-library/ostrstream-class.md)|Klasa opisuje obiekt, który kontroluje wstawiania elementów i zakodowany obiekty do bufora strumienia, klasy [strstreambuf —](../standard-library/strstreambuf-class.md).|
|[strstream, klasa](../standard-library/strstream-class.md)|Klasa opisuje obiekt, który kontroluje wstawienia i wydobycia elementów i obiektów zakodowanych przy użyciu bufor strumienia klasy [strstreambuf —](../standard-library/strstreambuf-class.md).|

## <a name="see-also"></a>Zobacz także

[\<strstream>](../standard-library/strstream.md)<br/>
[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
