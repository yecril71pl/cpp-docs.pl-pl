---
title: '&lt;strstream —&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <strstream>
dev_langs:
- C++
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f63ecc2f24431e54042a1b995762806f87c691da
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ltstrstreamgt"></a>&lt;strstream&gt;

Definiuje kilka klas, które obsługują operacje iostream sekwencji przechowywane w tablicy przydzielone `char` obiektu. Takie sekwencje są łatwo konwertowane do i z ciągów C.

## <a name="syntax"></a>Składnia

```cpp
#include <strstream>

```

## <a name="remarks"></a>Uwagi

Obiekty typu `strstream` współpracują `char` *, które są ciągami C. Użyj [ \<sstream — >](../standard-library/sstream.md) do pracy z obiektami typu [basic_string —](../standard-library/basic-string-class.md).

> [!NOTE]
> Klasy w \<strstream — > są przestarzałe. Rozważ użycie klasy w \<sstream — > zamiast tego.

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[strstreambuf, klasa](../standard-library/strstreambuf-class.md)|Klasa opisuje buforu strumienia, który kontroluje przesyłania elementów do i z sekwencję elementy przechowywane w `char` tablicy obiektów.|
|[istrstream, klasa](../standard-library/istrstream-class.md)|Klasa opisuje obiekt, który kontroluje wyodrębniania elementów i zakodowanego obiektów z buforu strumienia klasy [strstreambuf —](../standard-library/strstreambuf-class.md).|
|[ostrstream, klasa](../standard-library/ostrstream-class.md)|Klasa opisuje obiekt, który kontroluje wstawiania elementów i obiektów zakodowanych do buforu strumienia klasy [strstreambuf —](../standard-library/strstreambuf-class.md).|
|[strstream, klasa](../standard-library/strstream-class.md)|Klasa opisuje obiekt, który kontroluje wstawiania i wyodrębniania elementów i obiektów zakodowany przy użyciu buforu strumienia klasy [strstreambuf —](../standard-library/strstreambuf-class.md).|

## <a name="see-also"></a>Zobacz także

[\<strstream>](../standard-library/strstream.md)<br/>
[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
