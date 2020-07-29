---
title: '&lt;streambuf&gt;'
ms.date: 11/04/2016
f1_keywords:
- <streambuf>
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
ms.openlocfilehash: 1121bd4e782fca57588d05fb29b5b9b6cdec18e9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215611"
---
# <a name="ltstreambufgt"></a>&lt;streambuf&gt;

Dołącz standardowy nagłówek iostreams \<streambuf> , aby zdefiniować szablon klasy [basic_streambuf](../standard-library/basic-streambuf-class.md), który jest podstawowy dla operacji klas iostreams. Ten nagłówek jest zwykle dołączany przez inny z nagłówków iostreams; rzadko trzeba dołączyć go bezpośrednio.

## <a name="syntax"></a>Składnia

```cpp
#include <streambuf>
```

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|Specjalizacja `basic_streambuf` , która używa **`char`** jako parametrów szablonu.|
|[wstreambuf —](../standard-library/streambuf-typedefs.md#wstreambuf)|Specjalizacja `basic_streambuf` , która używa **`wchar_t`** jako parametrów szablonu.|

### <a name="classes"></a>Klasy

|Klasa|Opis|
|-|-|
|[Klasa basic_streambuf](basic-streambuf-class.md)|Szablon klasy opisuje abstrakcyjną klasę bazową dla tworzenia bufora strumienia, która kontroluje przekazywanie elementów do i z określonej reprezentacji strumienia.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostreams](../standard-library/iostreams-conventions.md)
